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
        <v-list class="ma-2" v-for="brewery in list" :key="brewery.id">
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Name :</v-list-item-title>
            </v-list-item-content>
            <v-list-item-content class="align-end">
              {{ brewery.name }}
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Street :</v-list-item-title>
            </v-list-item-content>
            <v-list-item-content class="align-end">
              {{ brewery.street }}
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>City :</v-list-item-title>
            </v-list-item-content>
            <v-list-item-content class="align-end">
              {{ brewery.city }}
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Zip :</v-list-item-title>
            </v-list-item-content>
            <v-list-item-content class="align-end">
              {{ brewery.postal_code }}
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
import useBrewList from "../composable/brew-list-api";
export default {
  setup() {
    const { val, list, submitted } = useBrewList();
    return { val, list, submitted };
  }  
};
</script>
