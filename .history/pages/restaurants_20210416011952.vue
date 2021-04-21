<template>
  <div class="container restaurant">
    <div class="restaurantheading">
      <h1>Restaurants</h1>
      <AppSelect @change="selectedRestaurant = $event" />
    </div>
    <AppRestaurantInfo :datasource="filteredRestaurants" />
  </div>
</template>

<script>
import AppSelect from "@/components/AppSelect.vue";
import AppRestaurantInfo from "@/components/AppRestaurantInfo.vue";
import { mapState } from "vuex";

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
    ...mapState(["fooddata"]),
    filteredRestaurants() {
      if (this.selectedRestaurant) {
        return this.fooddata.filter(el => {
          let name = el.name.toLowerCase();
          return name.includes(this.selectedRestaurant);
        });
      }
      return this.fooddata;
    }
  }
};
</script>

<style lang="scss" scoped>
.restaurant {
  .restaurantheading {
    margin: 100px 0 20px 200px;
    display: flex;
    align-items: center;
  }

  h1 {
    font-size: 30px;
    margin-right: 40px;
  }

  .filter {
    padding-right: 200px;
  }
}
</style>
