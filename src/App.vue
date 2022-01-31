<template>
  <div id="app">
    <header-content />
    <main-container :discs="discs"/>
  </div>
</template>

<script>
import axios from 'axios'

import HeaderContent from './components/HeaderContent.vue'
import MainContainer from './components/MainContainer.vue'


export default {
  name: 'App',
  components: {
    HeaderContent,
    MainContainer,
  },
  data() {
    return {
      discs : []
    }
  },
  mounted() {
    axios('https://flynn.boolean.careers/exercises/api/array/music')
    .then((result) => {
      this.discs = result.data.response
    })
  }
}
</script>

<style lang="scss">

  @import '@/style/main.scss';

</style>
