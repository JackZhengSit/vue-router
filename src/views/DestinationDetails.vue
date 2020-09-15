<template>
  <div>
    <GoBack />
    <section class="destination">
      <h1>{{destination.name}}</h1>
      <div class="destination-details">
        <img :src="require(`@/assets/${destination.image}`)" alt="destination.name" />
        <p>{{destination.description}}</p>
      </div>
    </section>
    <section class="experience">
      <h2>Top experience in {{destination.name}}</h2>
      <div class="cards" id="experience">
        <div v-for="experience in destination.experiences" :key="experience.slug" class="card">
          <router-link
            :to="{
                name:'experienceDetails',
                params:{experienceSlug:experience.slug,
                hash:'#experience'}
            }"
          >
            <img :src="require(`@/assets/${experience.image}`)" alt="experience.name" />
            <span class="card-text">{{experience.name}}</span>
          </router-link>
        </div>
      </div>
      <router-view :key="$route.path"></router-view>
    </section>
  </div>
</template>

<script>
import store from "@/store/store.js";
import GoBack from "@/components/GoBack";
export default {
  data() {
    return {};
  },
  props: {
    slug: {
      type: String,
      requireed: true
    }
  },
  computed: {
    destination() {
      return store.destinations.find(
        destination => destination.slug === this.slug
      );
    }
  },
  components: {
    GoBack
  }
};
</script>

<style scoped>
img {
  max-width: 600px;
  height: auto;
  width: 100%;
  max-height: 400px;
}
.destination-details {
  display: flex;
  justify-content: space-between;
}
p {
  margin: 0 40px;
  font-size: 20px;
  text-align: left;
}

.cards {
  display: flex;
  justify-content: center;
}

.cards img {
  max-width: 200px;
  width: 100%;
}

.card {
  padding: 0 20px;
  position: relative;
}

.card-text {
  position: absolute;
  top: 10%;
  left: 50%;
  transform: translate(-50%, 50%);
  color: white;
  font-size: 25px;
  font-weight: bold;
  text-decoration: none;
}
</style>