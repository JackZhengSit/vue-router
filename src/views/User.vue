<template>
  <div>
    <h1>Welcome {{user}}</h1>
    <p>
      <router-link :to="{
            name:'Invoices'
        }">Inovices</router-link>
    </p>
    <button @click="logout" class="btn">Log out</button>
  </div>
</template>

<script>
import store from "@/store/store.js";
export default {
  data() {
    return {
      user: store.user
    };
  },
  methods: {
    logout() {
      store.user = null;
      this.$router.push("/");
    }
  }
};
</script>

<style>
</style>