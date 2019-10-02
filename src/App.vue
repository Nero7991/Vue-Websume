<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <CustomNav Name="Oren Collaco" ProfileImage="oren.jpg" 
    v-bind:Items =  '{
    List: [
        {
            "Name": "value1",
            "prop2":"value2"
        },
        {
            "Name": "value3", 
            "prop2":"value4"
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

