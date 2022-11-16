<template>
  <div>
    <Header />
    <RightMenu />
    <MainWindow v-bind:orders="orders"/>
  </div>
</template>

<script>
  import Header from '@/components/Header.vue'
  import RightMenu from '@/components/RightMenu.vue'
  import MainWindow from '@/components/MainWindow.vue'
  import orders from './data/orders.json'

  export default {
    name: 'App',
    data() {
      return {
        orders
      }
    },  
    components: {
      Header, RightMenu, MainWindow
    }
  }
</script>

<style>
  @import './styles/index.css';
  @import url('https://fonts.googleapis.com/css2?family=Rubik:ital,wght@0,400;0,500;0,700;1,400&display=swap');
  body{
    margin: 0;
  }
  #app {
    box-sizing: border-box;
    font-family: 'Rubik', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }
</style>
