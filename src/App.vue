<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <CustomNav Name="Oren Collaco" ProfileImage="oren.jpg" 
    v-bind:MainContent =  '{
    Items: [
        {
            "Title": "Education",
            "Id": "education",
            "ContentText":"value2"
        },
        {
            "Title": "Experience",
            "Id": "experience", 
            "ContentText":"value4",
            SubItems: [
            {
              Id: "experience-konnect",
              Title: "Konnect Insights",
              Subtitle: "5 Months"
            },
            {
              Id: "experience-some",
              Title: "Some company",
              Subtitle: "6 Months"
            }
            ]
        }
    ]
}'
    />
  </div>
</template>

<script>
import CustomNav from './components/CustomNav.vue'

export default {
  name: 'app',
  components: {
    CustomNav
  }
}

</script>

