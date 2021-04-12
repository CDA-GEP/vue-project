<template>
    <div class="form-signin center">
        <form @submit.prevent="connect">
          <h1 class="h3 mb-3 fw-normal">Please sign in</h1>
          <div class="alert alert-danger" v-if="error">
              {{ error }}
          </div>
          <div class="form-floating">
          <input type="text" class="form-control" v-model="login" id="floatingInput" placeholder="Ex: ulee">
          <label for="floatingInput">Login</label>
          </div>
          <div class="form-floating">
          <input type="password" class="form-control" v-model="password" id="floatingPassword" placeholder="Password">
          <label for="floatingPassword">Password</label>
          </div>
          <div class="checkbox mb-3">
          <label>
              <input type="checkbox" value="remember-me"> Remember me
          </label>
          </div>
          <button class="w-100 btn btn-lg btn-primary" type="submit">Sign in</button>
          <p class="mt-5 mb-3 text-muted">&copy; 2017–2021</p>
        </form>
    </div>
</template>

<script>
export default {
  data(){
    return{
      login: '',
      password: '',
      error: null
    }
  },
  methods:{
    connect: async function(){
      const cryptedData = window.btoa(this.login + ':' + this.password)
      await fetch('http://localhost:90/gsb/user/' + this.login.toLowerCase(), {
        method: 'GET',
        headers:{
          "Content-type": "application/json",
          "Authorization": "Basic " + cryptedData
        },
        credentials: "include"
      })
      .then((response) => {
        if(response.status === 401){
          this.error = 'Bad login or password'
          console.log('Unauthorized')
        }else{
          this.$router.push('/')
          localStorage.setItem('username', this.login)
          console.log('user connecté')
          return response.json()
        } 
      })
      .then((data) => {
        console.log(data)
      })
    }
  }
}
</script>

<style scoped>
.form-signin {
  width: 100%;
  max-width: 330px;
  padding: 15px;
  margin: auto;
  height: 80vh;
}

.form-signin .checkbox {
  font-weight: 400;
}

.form-signin .form-floating:focus-within {
  z-index: 2;
}

.form-signin input[type="email"] {
  margin-bottom: -1px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}

.form-signin input[type="password"] {
  margin-bottom: 10px;
  border-top-left-radius: 0;
  border-top-right-radius: 0;
}
</style>