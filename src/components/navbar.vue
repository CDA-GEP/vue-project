<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Airbnb</a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <router-link class="nav-link" to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/about">About</router-link>
          </li>
           <li class="nav-item" v-if="user">
            <router-link class="nav-link" to="/dashboard">Dashboard</router-link>
          </li>
        </ul>
        {{ user }}
        <router-link v-if="!user" class="btn btn-outline-success" to="/login">Login</router-link>
        <router-link v-if="user" class="btn btn-outline-success" to="/logout">Logout</router-link>
      </div>
    </div>
  </nav>
</template>s

<script>
export default {
  data(){
    return{
      
    }
  },
  props:['user']
}
</script>

<style scoped>
nav{
  height: 10vh;
}
</style>