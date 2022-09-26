# Movie Pal

A curated list of repertory film screenings in Los Angeles. Built with Vue.js and Contentful CMS.

[View Demo Website](https://losangeles-moviepal.netlify.app/)

##  Project Setup
```
npm install
```

#### Compiles and hot-reloads for development
```
npm run serve
```

#### Compiles and minifies for production
```
npm run build
```

#### Lints and fixes files
```
npm run lint
```

Customize configuration, see [configuration reference](https://cli.vuejs.org/config/).

##  Contentful Setup

[Sign up](https://www.contentful.com/sign-up/) for Contentful account

#### Create an `.env` file at the root of your project and copy Space ID and Contentful Delivery API from Contentful > Settings > API Keys
```
VUE_APP_CONTENTFUL_SPACE_ID=
VUE_APP_CONTENTFUL_ACCESS_TOKEN=
```

#### Install Contentful CLI
```
npm install -g contentful-cli
```

#### Authenticate with CLI
```
contentful login
```
