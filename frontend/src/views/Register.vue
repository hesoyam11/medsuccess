<template>
  <div>
    <h1>Register</h1>
    <form @submit.prevent="register">
      <label for="username">Username</label>
      <div>
        <input id="username" type="text" v-model="username" required autofocus>
      </div>

      <label for="email">E-Mail Address</label>
      <div>
        <input id="email" type="email" v-model="email" required>
      </div>

      <label for="password">Password</label>
      <div>
        <input id="password" type="password" v-model="password" required>
      </div>

      <label for="password-confirm">Confirm Password</label>
      <div>
        <input id="password-confirm" type="password" v-model="password_confirmation" required>
      </div>

      <div>
        <button type="submit">Register</button>
      </div>
    </form>
  </div>
</template>

<script>
  export default {
    name: "Register",
    data() {
      return {
        username: "",
        email: "",
        password : "",
        password_confirmation : "",
      }
    },
    methods: {
      register: function() {
        let data = {
          username: this.username,
          email: this.email,
          password: this.password
        };
        this.$store.dispatch('register', data)
          .then(() => this.$router.push('/'))
          .catch(err => console.log(err))
      }
    }
  }
</script>

<style scoped>

</style>
