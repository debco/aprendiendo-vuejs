<template>
  <div id="app">
    <HeaderComponent></HeaderComponent>
      <!--<LastArticles></LastArticles>-->
      <router-view></router-view>
      
    <FooterComponent></FooterComponent>
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import FooterComponent from './components/FooterComponent.vue'

export default {
  name: 'app',
  components: {
    HeaderComponent,
    FooterComponent
  }
}
</script>

<style>
@import './assets/css/styles.css';
</style>
