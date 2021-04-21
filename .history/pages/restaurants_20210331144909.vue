<template>
  <div class="container restaurant">
    <div class="restaurantheading">
      <h1>Restaurants</h1>
      <AppSelect @change="selectedRestaurant = event"/>
    </div>
    <AppRestaurantInfo />
  </div>
</template>

<script>
import AppSelect from '@/components/AppSelect.vue';
import AppRestaurantInfo from '@/components/AppRestaurantInfo.vue';

export default {
  components: {
    AppRestaurantInfo,
    AppSelect
  },
  data() {
    return {
      selectedRestaurant: ''
    }
  }
};
</script>

<style lang="scss" scoped></style>
