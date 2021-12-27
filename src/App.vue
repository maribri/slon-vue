<style>
@import 'https://cdn.jsdelivr.net/npm/@mdi/font@4.x/css/materialdesignicons.min.css';
@import './assets/custom.css';
</style>
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
      <v-container class="mt-10">
        <v-row>
          <v-col
              cols="12"
              sm="4"
          >
            <DatePicker/>
          </v-col>
          <v-col
              cols="12"
              sm="4"
          ></v-col>
          <v-col
              cols="12"
              sm="4"
          >
            <Select/>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import DatePicker from './components/DatePicker';
import Select from './components/Select';

export default {
  name: 'App',

  components: {
    DatePicker,
    Select,
  },

  data: () => ({
    //
  }),
};
</script>
