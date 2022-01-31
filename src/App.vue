<template>
  <div id="app">
    <header-content />
    <main-container v-if="apiLoad" :discs="discs"/>
    <loader-content v-else/>
  </div>
</template>

<script>
import axios from 'axios'

import HeaderContent from './components/HeaderContent.vue'
import MainContainer from './components/MainContainer.vue'
import LoaderContent from './components/LoaderContent.vue'


export default {
  name: 'App',
  components: {
    HeaderContent,
    MainContainer,
    LoaderContent,
  },
  data() {
    return {
      discs : [],
      apiLoad: false,
    }
  },
  mounted() {
    setTimeout( () => {
      axios('https://flynn.boolean.careers/exercises/api/array/music')
        .then((result) => {
          this.discs = result.data.response
          this.apiLoad = true
      })
    },2000)
  }
}
</script>

<style lang="scss">

  @import '@/style/main.scss';

</style>
