<template>
  <div class="user-search-form">
    Here is UserSearchForm
    <b-field label="Name" grouped horizontal>
      <b-input placeholder="Search..." type="search" v-model="name"></b-input>
      <p class="control">
        <!-- <b-button class="button is-primary">Search</b-button> -->
      </p>
    </b-field>
    <b-field label="Age" grouped horizontal>
      <b-input placeholder="Search..." type="search"></b-input>
      <p class="control">
        <!-- <b-button class="button is-primary">Search</b-button> -->
      </p>
    </b-field>
    <b-field label="Sex" grouped horizontal>
      <b-input placeholder="Search..." type="search"></b-input>
      <p class="control">
        <b-button class="button is-primary" @click="onClickButton"
          >Search</b-button
        >
      </p>
    </b-field>
  </div>
</template>

<script>
//import Home from "../../views/Home.vue";
export default {
  name: "mainComponent",
  data() {
    return {
      searchQuery: null,
      resources: [],
      name: "",
      age: 0,
      sex: false
    };
  },

  methods: {
    onClickButton() {
      this.$emit("clicked", this.name);
    }
  }
};
</script>

<style scoped>
.user-search-form {
  height: 200px;
  background-color: yellow;
}
</style>
