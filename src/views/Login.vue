<template>
  <section>
    <div class="">
      <pre>user</pre>
      <form>
        <div class="row">
            <input type="text" name="" v-model="form.email">
        </div>
        <br>
        <div class="row">
            <input type="password" name="" v-model="form.password">
        </div>
        <br>
        <div class="row">
          <button type="button" name="button" @click="login">
            Login
          </button>
        </div>
      </form>
    </div>
  </section>
</template>
<script>
  import axios from 'axios'
  axios.defaults.withCredentials = true
  axios.defaults.baseURL = 'http://localhost:8000'
  export default {
    data(){
      return {
        user: null,
          form: {
            email:'juan@gmail.com',
            password: '123456'
          }
      }
    },
    methods: {
      async login(){
        await axios.get('/sanctum/csrf-cookie')
            axios.post('/login', this.form).then(res => {
              console.log(res)  
            }).catch(e => {
              console.log(e)          
            })
      }
    }
  }
</script>
