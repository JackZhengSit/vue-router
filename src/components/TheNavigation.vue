<template>
  <nav id="nav">
    <!-- <router-link to="/">Home</router-link>
    <router-link to="/brazil">Brazil</router-link>
    <router-link to="/panama">Panama</router-link>
    <router-link to="/hawaii">Hawaii</router-link>
    <router-link to="/jamaica">Jamaica</router-link>-->
    <p class="logo">The vue router travel App</p>
    <ul class="nav-links">
      <li class="links">
        <router-link to="/">Home</router-link>
      </li>
      <li v-for="destination in destinations" :key="destination.name" class="links">
        <router-link
          :to="{
         name:'DestinationDetails',
         params:{slug:destination.slug}
          }"
        >{{destination.name}}</router-link>
      </li>
      <li class="links">
        <router-link to="/user">Dashboard</router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
import store from "@/store/store.js";
export default {
  data() {
    return {
      // slug: this.$route.params.slug,
      destinations: store.destinations
    };
  }
};
</script>

<style lang="scss" scoped>
#nav {
  display: flex;
  align-items: center;
  a {
    font-weight: bold;
    text-decoration: none;
    color: #2c3e50;
    padding: 0 10px;
    &.router-link-exact-active {
      color: rgb(85, 26, 139);
    }
  }
  position: sticky;
  top: 0;
  background-color: white;
  border-bottom: 1px solid grey;
  z-index: 1;
}
.nav-links {
  display: flex;
}

.links {
  padding-right: 20px;
  list-style: none;
}

.links:hover {
  text-decoration: underline;
}
.logo {
  font-size: 20px;
  color: purple;
  font-weight: bold;
}
</style>>
