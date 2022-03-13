<template>
  <div>
    <v-btn color="primary" @click="fetchData">get data</v-btn>
    <v-card class="mx-auto" max-width="300" tile>
      <v-list dense>
        <v-subheader>USERS</v-subheader>
        <v-list-item-group color="primary">
          <v-list-item v-for="(item, i) in userList" :key="i">
            <v-list-item-icon>
              <v-icon v-text="i + 1"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="item.name"></v-list-item-title>
              <v-list-item-subtitle v-text="item.email"></v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-card>
  </div>
</template>

<script>
//axios 라이브러리 import
import axios from "axios";
export default {
  name: "IndexPage",
  data() {
    return {
      userList: null,
    };
  },
  methods: {
    fetchData: function () {
      axios
        .get("https://jsonplaceholder.typicode.com/users/")
        .then((response) => {
          this.userList = response.data;
        })
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>
