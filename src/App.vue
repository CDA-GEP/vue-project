<template>
  <navbar v-bind:user="user"></navbar>
  <div class="container">
    <router-view v-bind:user="user"></router-view>
  </div>
  <footer-app></footer-app>
  
</template>

<script>
import navbar from '@/components/navbar'
import footerApp from '@/components/footer'
export default {
  name: 'app',
  components:{
    navbar,
    footerApp
  },
  data(){
    return{
        user: null
    }
  },
  mounted(){
      this.user = localStorage.getItem('username')
  }
}
</script>

<style>
  h1{
    color: green;
  }

  .center{
      display: flex;
      align-items: center;
      justify-content: center;
  }
</style>