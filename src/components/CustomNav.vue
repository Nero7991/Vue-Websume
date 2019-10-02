<template>
  <b-container fluid>
    <b-row>
      <b-col cols="3">
        <b-navbar v-b-scrollspy:scrollspy-nested class="flex-column">
          <b-navbar-brand href="#">{{ Name }}</b-navbar-brand>
          <b-nav v-if="MainContent.Items.length" pills vertical>
            <div v-for="i in MainContent.Items.length" v-bind:key="i">
              <b-nav-item
                v-bind:href="'#' + MainContent.Items[i - 1].Id"
              >{{ MainContent.Items[i - 1].Title }}</b-nav-item>
              <b-nav v-if="MainContent.Items[i-1].SubItems" pills vertical>
                <b-nav-item
                  v-for="j in MainContent.Items[i-1].SubItems.length"
                  v-bind:key="j"
                  class="ml-3 my-1"
                  v-bind:href="'#' + MainContent.Items[i-1].SubItems[j-1].Id"
                >{{ MainContent.Items[i-1].SubItems[j-1].Title }}</b-nav-item>
              </b-nav>
            </div>
          </b-nav>
        </b-navbar>
      </b-col>

      <b-col cols="9">
        <div id="scrollspy-nested" style="position:relative; height:100vh; overflow-y:auto">
          <div v-if="MainContent.Items.length">
            <div v-for="i in MainContent.Items.length" v-bind:key="i" class="screen-height">
              <h4 v-bind:id="MainContent.Items[i - 1].Id">{{ MainContent.Items[i - 1].Title }}</h4>
              <p>{{ MainContent.Items[i - 1].ContentText }}</p>
              <div v-if="MainContent.Items[i-1].SubItems">
                <div v-for="j in MainContent.Items[i-1].SubItems.length" v-bind:key="j">
                  <h5
                    v-bind:id="MainContent.Items[i-1].SubItems[j-1].Id"
                  >{{ MainContent.Items[i-1].SubItems[j-1].Title }}</h5>
                  <p>{{ MainContent.Items[i-1].SubItems[j-1].Subtitle }}</p>
                </div>
              </div>
            </div>
          </div>
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
    MainContent: Object
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
        `
    };
  }
};
Vue.component("item-content", {
  template:
    '<div class="screen-height"><h4 v-bind:id="Id" style>{{ Title }}</h4><p>{{ Content }}</p></div>',
  props: ["Title", "Id", "Content"]
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