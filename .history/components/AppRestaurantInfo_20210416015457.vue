<template>
  <section class="restaurantinfo">
    <div v-for="store in datasource" :key="store.id">
      <h2>{{ store.name }}</h2>
      <p>Delivery Time {{ store.deliveryTime }}</p>
      <p>{{ store.rating }}</p>
      <p v-if="store.freeDelivery" class="label">
        <span>Free Delivery</span>
      </p>

      <div class="row">
        <div
          v-for="menuitem in store.menu"
          :key="menuitem.id"
          class="items"
          :style="`background: url(${menuitem.img}) no-repeat center center`"
        >
          <div class="iteminfo">
            <div>
              <h4>{{ menuitem.item }}</h4>
              <p>{{ priceFormatting(menuitem.price) }}</p>
            </div>
            <nuxt-link :to="`/items/${menuitem.id}`">
              <button class="ghost">View Item</button>
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
// import { mapState } from "vuex";

export default {
  props: {
    datasource: {
      type: [Array, Object]
    }
  },

  // computed: {
  //   ...mapState(["fooddata"])
  // },

  methods: {
    priceFormatting(item) {
      return "$" + item.toFixed(2);
    }
  }
};
</script>

<style lang="scss" scoped>
section.restaurantinfo {
  padding: 20px 200px;

  .items {
    position: relative;
    height: 250px;
    border-radius: 5px;
    box-shadow: 2px 6px 6px 0 rgb(215, 215, 215);
    background-size: cover;
  }

  .iteminfo {
    display: flex;
    justify-content: space-between;
    position: absolute;
    bottom: 0;
    padding: 15px;
    width: 100%;
    background: white;
  }
}
</style>
