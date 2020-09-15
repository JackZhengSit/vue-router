<template>
  <div class="login">
    <h1>Login</h1>
    <div class="form">
      <label for="username">Username</label>
      <input v-model="username" type="text" name="username" class="input" />
      <label for="password">Password</label>
      <input v-model="password" type="password" class="input" />
      <button class="btn" @click="Login">Login</button>
    </div>
  </div>
</template>

<script>
import store from "@/store/store.js";
export default {
  data() {
    return {
      username: null,
      password: null
    };
  },
  methods: {
    Login() {
      //Authenticate against API
      store.user = this.username;
      //   this.$router.push("/user");
      const redirectPath = this.$route.query.redirect || "/";
      this.$router.push(redirectPath);
    }
  }
};
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  max-width: 400px;
  margin: 0 auto;
}
</style>