<script setup>

import Footer from './components/Footer.vue';
import Menu from './components/Menu.vue'
import data from './data/data.json'
import WhatsApp from './components/WhatsApp.vue';
import Loading from './components/Loading.vue';

// Paleta de Colores https://www.color-hex.com/color-palette/31535

const theme = {
  first: '#ffd8ff',
  second: '#890089',
  third: '#e7008a',
  fourth: 'violet',
}

</script>

<template>

  <div class="app-container">

    <WhatsApp
    :data="data"    
    />

    <Loading/>

    <Menu
    :data="data"
    :theme="theme"
    />    

    <router-view
    :data="data"
    :theme="theme"
    />
    
    <Footer
    :data="data"
    :theme="theme"
    />

  </div>

 
</template>

<style lang='scss' scoped>

  .app-container {
    width: 100%;
    height: auto;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;

  }

</style>
