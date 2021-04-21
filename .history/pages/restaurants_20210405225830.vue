<template>
  <div class="container restaurant">
    <div class="restaurantheading">
      <h1>Restaurants</h1>
      <AppSelect @change="selectedRestaurant = $event" />
      <pre>{{ $data }}</pre>
    </div>
    <AppRestaurantInfo />
  </div>
</template>

<script>
import AppSelect from "@/components/AppSelect.vue";
import AppRestaurantInfo from "@/components/AppRestaurantInfo.vue";
import { mapState } from 'vuex';

export default {
  components: {
    AppRestaurantInfo,
    AppSelect
  },
  data() {
    return {
      selectedRestaurant: ""
    };
  },
  computed: {
    ...mapState([
      'fooddata',
    ]),
    filterRestaurants() {

    }
  },
};
</script>

<style lang="scss" scoped></style>
