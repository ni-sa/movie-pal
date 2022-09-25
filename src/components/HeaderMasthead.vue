<template>
  <div class="header-masthead">
    <b-row>
      <b-col>
        <hr class="top" />
        <div class="heading">
          <b-row>
            <b-col lg="auto" order="2" order-lg="1">
              <h1>{{ masthead.cityName }}</h1>
            </b-col>
            <b-col lg="auto" order="1" order-lg="2">
              <img
                class="mascot"
                :alt="masthead.appName"
                :src="masthead.mascot.url"
              />
            </b-col>
            <b-col lg="auto" order="3" order-lg="3">
              <h1>{{ masthead.appName }}</h1>
            </b-col>
          </b-row>
        </div>
        <hr class="middle" />
        <div class="description">
          {{ masthead.description }}
        </div>
        <div class="additional-info">
          <span class="group-name">
            <span class="label">Developed by</span>
            <a :href="masthead.personalLink" blank="_blank">{{ masthead.personalName }}</a>
          </span>
          <span class="pipe">|</span>
          <span class="group-github">
            <span class="label">View Code on</span>
            <a :href="masthead.githubLink" target="_blank">GitHub <b-icon icon="github" aria-hidden="true"></b-icon></a>
          </span>
        </div>
        <hr class="bottom" />
        <hr class="bottom" />
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  data() {
    // will store fetched data here
    return {
      masthead: [],
    };
  },
  async created() {
    // will call method to fetch here
    this.masthead = await this.getMasthead();
  },
  methods: {
    // will define function to fetch data here
    getMasthead: async () => {
      const query = `{
        mastheadCollection {
          items {
            sys {
              id
            }
            appName
            cityName
            mascot {
              url
            }
            description
            personalName
            personalLink
            githubLink
          }
        }
      }`;
      const fetchUrl = `https://graphql.contentful.com/content/v1/spaces/${process.env.VUE_APP_CONTENTFUL_SPACE_ID}`;
      const fetchOptions = {
        method: "POST",
        headers: {
          Authorization: `Bearer ${process.env.VUE_APP_CONTENTFUL_ACCESS_TOKEN}`,
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          query,
        }),
      };
      try {
        const response = await fetch(fetchUrl, fetchOptions).then((response) =>
          response.json()
        );
        return response.data.mastheadCollection.items[0];
      } catch (error) {
        throw new Error("Could not receive the data from Contentful!");
      }
    },
  },
};
</script>

<style lang="scss"></style>
