<template>
  <v-app>
    <v-app-bar app>
      <v-toolbar-title class="headline text-uppercase">
        <router-link to="/" tag="span" style="cursor: pointer">
          Movie Man
        </router-link>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-flex xs12 sm6 md3>
        <v-text-field label="Movie Name" v-model="searchString"> </v-text-field>
      </v-flex>
      <v-btn :disabled="!dataAvailable" @click="searchMovie">
        <span class="mr-2">Search</span>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      searchString: "",
    };
  },
  methods: {
    searchMovie() {
      this.$router.push("/search/" + this.searchString);
      this.searchString = "";
    },
  },
  computed: {
    dataAvailable() {
      return this.searchString !== null && this.searchString !== "";
    },
  },
};
</script>