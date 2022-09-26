# Movie Pal

A curated list of repertory film screenings in Los Angeles. Built with Vue.js and Contentful CMS.

[View Demo Website](https://losangeles-moviepal.netlify.app/)

![Screenshot](https://user-images.githubusercontent.com/34425888/192181220-7f9f291d-793f-4f5a-bb0f-c025c1b44bd3.png)

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

#### Create an `.env` file at the root of your project
Copy `Space ID` from Settings > General settings and `Contentful Delivery API` from Settings > API keys
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
