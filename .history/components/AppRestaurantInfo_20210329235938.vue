<template>
  <section class="restaurantinfo">
    <div v-for="store in fooddata" :key="store.id">
      <h2>{{ store.name }}</h2>
    </div>
  </section>
</template>

<script>
import { mapState } from "vuex";

export default {
  computed: {
    ...mapState(["fooddata"])
  }
};
</script>

<style lang="scss" scoped></style>
