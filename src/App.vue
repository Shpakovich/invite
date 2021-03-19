<template>
  <v-app>
      <v-main class="bg-black">
          <HelloWorld/>
      </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
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
