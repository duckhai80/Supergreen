<template>
  <div class="container restaurant">
    <div class="restaurantheading">
      <h1>Restaurants</h1>
      <AppSelect />
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
  }
};
</script>

<style lang="scss" scoped></style>
