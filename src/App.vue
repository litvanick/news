<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <NewsView v-for="n in news" v-bind="n" v-bind:key="title"></NewsView>
    </v-main>
  </v-app>
</template>

<script>
import NewsView from './components/NewsView';

export default {
  name: 'App',
  components: {
    NewsView,
  },
  data: () => ({
    url: 'https://newsapi.org/v2/top-headlines?country=us&apiKey=d7f41a32c26b4bbfb596d58b1a54c766',
    news: [],
  }),
  methods: {
    async loadNews() {
      let response = await this.axios.get(this.url)
      this.news = response.data.articles
    }
  },
  onMounted() {
    this.loadNews()
  },
};
</script>
