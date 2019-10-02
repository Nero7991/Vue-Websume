<template>
  <b-container fluid>
    <b-row>
      <b-col cols="3">
        <b-navbar v-b-scrollspy:scrollspy-nested class="flex-column">
          <b-navbar-brand href="#">{{ Name }}</b-navbar-brand>
          <b-nav v-if="Items.List.length" pills vertical>
            <b-nav-item v-for="i in Items.List.length" v-bind:key="i" href="#item-1">{{ Items.List[i - 1].Name }}</b-nav-item>
            <b-nav pills vertical>
              <b-nav-item class="ml-3 my-1" href="#item-1-1">Item 1-1</b-nav-item>
              <b-nav-item class="ml-3 my-1" href="#item-1-2">Item 1-2</b-nav-item>
            </b-nav>
            <b-nav-item href="#item-2">Item 2</b-nav-item>
            <b-nav-item href="#item-3">Item 3</b-nav-item>
            <b-nav pills vertical>
              <b-nav-item class="ml-3 my-1" href="#item-3-1">Item 3-1</b-nav-item>
              <b-nav-item class="ml-3 my-1" href="#item-3-2">Item 3-2</b-nav-item>
            </b-nav>
          </b-nav>
        </b-navbar>
      </b-col>

      <b-col cols="9">
        <div id="scrollspy-nested" style="position:relative; height:100vh; overflow-y:auto">
          <div class="screen-height">
            <h4 id="item-1" style>Item 1</h4>
            <p>{{ text }}</p>
          </div>
          <h5 id="item-1-1" style>Item 1-1</h5>
          <p>{{ text }}</p>
          <h5 id="item-1-2" style>Item 2-2</h5>
          <p>{{ text }}</p>
          <h4 id="item-2" style>Item 2</h4>
          <p>{{ text }}</p>
          <h4 id="item-3" style>Item 3</h4>
          <p>{{ text }}</p>
          <h5 id="item-3-1" style>Item 3-1</h5>
          <p>{{ text }}</p>
          <h5 id="item-3-2" style>Item 3-2</h5>
          <p>{{ text }}</p>
        </div>
      </b-col>
    </b-row>
  </b-container>
</template>


<script>
import Vue from "vue";

export default {
  name: "CustomNav",
  components: {},
  props: {
    Name: String,
    ProfileURL: String,
    Items: Object,
  },
  data() {
    return {
      text: `
          Quis magna Lorem anim amet ipsum do mollit sit cillum voluptate ex nulla
          tempor. Laborum consequat non elit enim exercitation cillum aliqua
          consequat id aliqua. Esse ex consectetur mollit voluptate est in duis
          laboris ad sit ipsum anim Lorem. Incididunt veniam velit elit elit veniam
          Lorem aliqua quis ullamco deserunt sit enim elit aliqua esse irure. Laborum
          nisi sit est tempor laborum mollit labore officia laborum excepteur
          commodo non commodo dolor excepteur commodo. Ipsum fugiat ex est consectetur
          ipsum commodo tempor sunt in proident.
          Quis magna Lorem anim amet ipsum do mollit sit cillum voluptate ex nulla
          tempor. Laborum consequat non elit enim exercitation cillum aliqua
          consequat id aliqua. Esse ex consectetur mollit voluptate est in duis
          laboris ad sit ipsum anim Lorem. Incididunt veniam velit elit elit veniam
          Lorem aliqua quis ullamco deserunt sit enim elit aliqua esse irure. Laborum
          nisi sit est tempor laborum mollit labore officia laborum excepteur
          commodo non commodo dolor excepteur commodo. Ipsum fugiat ex est consectetur
          ipsum commodo tempor sunt in proident.
          Quis magna Lorem anim amet ipsum do mollit sit cillum voluptate ex nulla
          tempor. Laborum consequat non elit enim exercitation cillum aliqua
          consequat id aliqua. Esse ex consectetur mollit voluptate est in duis
          laboris ad sit ipsum anim Lorem. Incididunt veniam velit elit elit veniam
          Lorem aliqua quis ullamco deserunt sit enim elit aliqua esse irure. Laborum
          nisi sit est tempor laborum mollit labore officia laborum excepteur
          commodo non commodo dolor excepteur commodo. Ipsum fugiat ex est consectetur
          ipsum commodo tempor sunt in proident.
        `
    };
  }
};
Vue.component('content-item', {
  template: '<div class="screen-height"><h4 v-bind:id="Name.toLowerCase()" style>{{ Name }}</h4><p>{{ Content }}</p></div>',
  props: ['Name', 'Content']
});
</script>

<style scoped>
.bg-color {
  background-color: #b84d17 !important;
}
body {
  height: 100%;
}

.screen-height {
  height: 100vh;
}
</style>