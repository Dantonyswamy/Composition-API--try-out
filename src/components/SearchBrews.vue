<template>
  <v-container>
    <v-row align="center" justify="center">
      <v-col cols="6">
        <v-row>
          <h2>Brew Search</h2>
        </v-row>
        <v-form @submit.prevent="submitted">
          <v-row>
            <v-text-field
              solo
              label="Search a pub"
              prepend-inner-icon="search"
              v-model="val"
            ></v-text-field>
          </v-row>
          <v-row align="center" justify="center">
            <v-btn small rounded outlined color="primary" @click="submitted">
              Submit
            </v-btn>
          </v-row>
        </v-form>
        <v-list class="ma-2">
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Name :</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Street :</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>City :</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Zip :</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      val: "",
      breweries: []
    };
  },
  methods: {
    async submitted() {
      const response = await fetch(
        `https://api.openbrewerydb.org/breweries/?by_name=${this.val}`
      );
      const json = await response.json();
      console.log(json);
    }
  }
};
</script>
