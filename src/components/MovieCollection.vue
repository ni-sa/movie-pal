<template>
  <div class="movie-collection">
    <b-row>
      <b-col md="6" lg="4" xl="3" v-for="movie in movies" v-bind:key="movie.sys.id">
        <b-card :img-alt="movie.title" :img-src="movie.poster.url + '?w=600'" img-top>
            <div class="title">{{ movie.title }} <span class="year"> ({{ movie.year }})</span></div>
            <div class="director">Dir: {{ movie.director }}</div>
            <div class="format">Format: {{ movie.format }}</div>            
            <hr>
            <div class="date">{{ movie.date | moment("ddd, ll") }}</div>
            <div class="time">{{ movie.date | moment("LT") }}</div>
            <hr>
            <div class="venue">{{ movie.venue }}</div>            
            <a :href="movie.link" target="_blank" class="link">More Info <b-icon icon="arrow-right" aria-hidden="true"></b-icon></a>
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
export default {
  data() {
    // will store fetched data here
    return {
      movies: [],
    };
  },
  async created() {
    // will call method to fetch here
    this.movies = await this.getMovies();
  },
  methods: {
    // will define function to fetch data here
    getMovies: async () => {
      const query = `{
        movieCollection(order: date_ASC) {
          items {
            sys {
              id
            }
            title
            year
            director
            format
            date
            venue
            link
            poster {
                url
            }
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
        return response.data.movieCollection.items;
      } catch (error) {
        throw new Error("Could not receive the data from Contentful!");
      }
    },
  },
};
</script>

<style lang="scss"></style>