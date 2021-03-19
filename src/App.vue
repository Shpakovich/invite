<template>
  <v-app>
      <v-main class="bg-black">
          <MainPage/>
      </v-main>
  </v-app>
</template>

<script>
import MainPage from './components/MainPage';

export default {
  name: 'App',

  components: {
      MainPage,
  },

    head () {
        return {
            title: 'test',
            meta: [
                {
                    name: 'viewport',
                    content: 'width=device-width,initial-scale=1.0,minimum-scale=1.0'
                }
            ]
        }
    }
};
</script>
