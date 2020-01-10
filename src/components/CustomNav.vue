<template>
    <b-container fluid>
        <b-row>
            <div id="Sidebar" class="col-sm-4 col-md-3 bg-color ">
                <!-- <slider
                                      :width="300"
                                      format="push"
                                      direction="left"
                                      :opacity="0.15"
                                      :links="[{'id': 1, 'text': 'Link 1', 'url': 'https://github.com'}, {'id': 2, 'text': 'Link 2', 'url': 'https://github.com'}]"
                                    > -->
                <b-navbar toggleable="sm" v-b-scrollspy:scrollspy-nested class="flex-column nav-holder navbar-fixed-top">
                    <b-navbar-toggle target="nav-text-collapse"></b-navbar-toggle>
                    <!-- <b-navbar-brand href="#">{{ Name }}</b-navbar-brand> -->
                    <b-collapse id="nav-text-collapse" is-nav>
                        <!-- <span class="d-block d-lg-none">{{ Name }}</span> -->
                        <span class="d-none d-sm-block" id="ProfileImage">
                                            <img
                                              class="img-fluid img-profile rounded-circle mx-auto mb-2"
                                              :src="require (`@/assets/${ProfileURL}`)"
                                              alt
                                            />
                                          </span>
                        <b-nav v-if="MainContent.Items.length" pills vertical id="IndexHolder">
                            <div v-for="i in MainContent.Items.length" v-bind:key="i">
                                <b-nav-item class="IndexItem" v-bind:href="'#' + MainContent.Items[i - 1].Id">{{ MainContent.Items[i - 1].Title }}</b-nav-item>
                                <b-collapse id="Something">
                                    <b-nav v-if="MainContent.Items[i-1].SubItems" pills vertical>
                                        <b-nav-item v-if="MainContent.Items[i-1].SubItems[j-1].Subtitle.length && (MainContent.Items[i-1].SubItems[j-1].IsDisplayed != false) && MainContent.Items[i-1].SubItems" v-for="j in MainContent.Items[i-1].SubItems.length" v-bind:key="j" class="ml-3 my-1"
                                            v-bind:href="'#' + MainContent.Items[i-1].SubItems[j-1].Id">{{ MainContent.Items[i-1].SubItems[j-1].Title }}</b-nav-item>
                                    </b-nav>
                                </b-collapse>
                            </div>
                        </b-nav>
                    </b-collapse>
                </b-navbar>
            </div>
            <div id="MainContent" class="col-sm-8 col-md-9">
                <div id="scrollspy-nested" style="position:relative; height:100vh; overflow-y:auto">
                    <div v-if="MainContent.Items.length">
                        <div v-for="i in MainContent.Items.length" v-bind:key="i" class="screen-height">
                            <div class="dummy-nav" v-bind:id="MainContent.Items[i - 1].Id"></div>
                            <h4 class="ContentHeader" v-bind:id="MainContent.Items[i - 1].Id">{{ MainContent.Items[i - 1].Title }}</h4>
                            <p v-if="MainContent.Items[i - 1].ContentText.length" class="ContentText">{{ MainContent.Items[i - 1].ContentText }}</p>
                            <div v-if="MainContent.Items[i-1].SubItems">
                                <div class="project-holder" v-for="j in MainContent.Items[i-1].SubItems.length" v-bind:key="j">
                                    <h5 v-if="MainContent.Items[i-1].SubItems[j-1].Title.length && (MainContent.Items[i-1].SubItems[j-1].IsDisplayed != false)" class="SubContentHeader" v-bind:id="MainContent.Items[i-1].Id">{{ MainContent.Items[i-1].SubItems[j-1].Title }}</h5>
                                    <h6 v-if="MainContent.Items[i-1].SubItems[j-1].Subtitle.length && (MainContent.Items[i-1].SubItems[j-1].IsDisplayed != false)" class="SubContentTitle" v-bind:id="MainContent.Items[i-1].Id">{{ MainContent.Items[i-1].SubItems[j-1].Subtitle }}</h6>
                                    <p v-if="MainContent.Items[i-1].SubItems[j-1].ContentText && (MainContent.Items[i-1].SubItems[j-1].IsDisplayed) != false" class="SubContentText">{{ MainContent.Items[i-1].SubItems[j-1].ContentText }}</p>
                                    <div class="img-project-holder" v-if="MainContent.Items[i-1].SubItems[j-1].ImageCount">
                                        <!-- <img v-for="k in MainContent.Items[i-1].SubItems[j-1].ImageCount" v-bind:key="k" class="img-fluid img-project col-sm-12 col-md-4" :src="require (`@/assets/${MainContent.Items[i-1].SubItems[j-1].Id + k + '.jpeg'}`)" alt /> -->
                                        <b-carousel class="CarouselHolder" id="carousel-1" v-model="slide" :interval="3000" controls indicators background="transparent" style="text-shadow: 1px 1px 2px #333;" @sliding-start="onSlideStart" @sliding-end="onSlideEnd">
                                            <b-carousel-slide v-bind:text="MainContent.Items[i-1].SubItems[j-1].ImageText" class="CarouselElement" v-for="k in MainContent.Items[i-1].SubItems[j-1].ImageCount" v-bind:key="k" :img-src="require (`@/assets/${MainContent.Items[i-1].SubItems[j-1].Id + k + '.jpeg'}`)"></b-carousel-slide>
                                        </b-carousel>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
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
    template: '<div class="screen-height"><h4 v-bind:id="Id" style>{{ Title }}</h4><p>{{ Content }}</p></div>',
    props: ["Title", "Id", "Content"]
});
// var vm = new Vue({
//   el: '#Sidebar',
//   data: {
//      width:'200px'
//   },
//   computed: {
//     computedWidth: function () {
//       return '100px';
//     }
//   },
//   methods: {
//     changeWidth: function (event) {
//       this.width='100px';
//     }
//   }
// })
</script>

<style scoped>
#Sidebar {
    /* max-width: 22% !important; */
    /* position: fixed; */
    /* min-height: 100vh; */
}

#MainContent {
    /* margin-left: 25% */
    padding-left: 0px;
    padding-right: 0px;
}

#ProfileImage {
    padding-top: 20%;
}

#IndexHolder {
    padding-top: 10%;
    text-transform: uppercase;
    font-weight: 800;
    font-size: 0.9rem;
    letter-spacing: 0.05rem;
    align-items: flex-start;
}

.ContentHeader {
    font-size: 1.5rem;
    padding-top: 3%;
    padding-left: 2%;
}

.ContentText {
    font-size: 1rem;
    padding-left: 2%;
    padding-top: 1%;
}

.SubContentHeader {
    font-size: 1.18rem;
    font-weight: 400;
    padding-top: 2%;
    padding-left: 3%;
}

.SubContentTitle {
    font-size: 1.12rem;
    font-weight: 300;
    padding-top: 0%;
    padding-left: 3%;
}

.SubContentText {
    font-size: 1rem;
    padding-left: 3%;
    padding-top: 1%;
}

.IndexItem {
    /* padding-top: 7%; */
}

#nav-text-collapse {
    flex-direction: column;
    background-color: #8a4522 !important;
    z-index: 100;
    border-radius: 10px;
}

.nav-link.active {
    background-color: #ff810096 !important;
    z-index: 200;
}

.nav-item a {
    color: rgb(245, 245, 245) !important;
}

.nav-link {
    display: block;
    padding: 0.6rem 2em;
}

.bg-color {
    background-color: #8a4522 !important;
}

body {
    height: 100%;
    font-family: sans-serif;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
}

.screen-height {
    min-height: 100vh;
    padding-right: 3%;
    padding-left: 2%;
}

.img-profile {
    max-width: 11rem;
    max-height: 11rem;
    border: 0.5rem solid rgba(255, 255, 255, 0.2);
    object-fit: cover;
    width: 10rem;
    height: 10rem;
}

.img-project {
    border: 0.5rem solid rgba(255, 255, 255, 0.2);
    object-fit: cover;
    /* width: 32%; */
    height: 180px;
    border-radius: 12px;
    padding-left: unset;
    padding-right: unset;
}

.project-holder {
    /* padding-bottom: 2rem; */
}

.img-project-holder {
    padding-left: 1rem;
    padding-bottom: 2rem;
}

.dummy-nav {
    display: block;
    position: relative;
    width: 100%;
    height: 1px;
    /* top: 56px; */
    z-index: 0;
}

@media screen and (max-width: 576px) {
    #Sidebar {
        position: fixed;
        min-height: unset;
        z-index: 2;
    }
    .dummy-nav {
        display: block;
        position: relative;
        width: 100%;
        height: 56px;
        /* top: 56px; */
        z-index: 0;
    }
    .nav-holder {
        align-items: flex-start;
    }
    .CarouselHolder {
        max-height: 300px;
        height: 300px;
        border-radius: 10px;
    }
    .CarouselElement {
        max-height: 300px;
        height: 300px;
        border-radius: 10px;
    }
}

@media screen and (min-width: 577px) and (max-width: 991px) {
    .CarouselHolder {
        max-height: 300px;
        height: 300px;
        border-radius: 10px;
    }
    .CarouselElement {
        max-height: 300px;
        height: 300px;
        border-radius: 10px;
    }
}

@media screen and (min-width: 992px) {
    #Sidebar {
        max-width: 22% !important;
    }
    #MainContent {
        min-width: 78% !important;
    }
    .CarouselHolder {
        max-height: 500px;
        height: 500px;
        border-radius: 10px;
    }
    .CarouselElement {
        max-height: 500px;
        height: 500px;
        border-radius: 10px;
    }
}

</style>