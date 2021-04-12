<template>
  <div>
      ceci est la page 'about'
      <h2 v-if="user">{{ user }}</h2>
      <h2 v-else>Bonjour</h2>

  </div>
</template>

<script>
export default {
  data(){
    return{
      user: null, //string
      ok: false,//boolean
    }
  }
}
</script>

<style scoped>
h1{
  color: red;
}
</style>