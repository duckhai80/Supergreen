<template>
  <div>
    <section class="masthead" role="img" aria-label="Image Description">
      <h1>
        Supergreen
      </h1>
      <button>
        See restaurants
      </button>
    </section>
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
  </div>
</template>

<script>
export default {
  setup() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
.masthead {
  padding: 40px;
  width: 100%;
  height: 96vh;
  background-size: cover !important;
  background: radial-gradient(
      ellipse at center,
      rgba(0, 0, 0, 0) 0%,
      rgba(0, 0, 0, 0) 37%,
      rgba(0, 0, 0, 0.65) 100%
    ),
    url(~assets/headerimg.jpg) no-repeat center center scroll;
  overflow: hidden;
}

h1 {
  margin-bottom: 40px;
  line-height: 1;
  text-shadow: 1px 2px 4px rgba(0, 0, 0, 0.8);
  font-style: normal;
  font-size: 8vmin;
  font-weight: bold;
  color: #eee;
  letter-spacing: 0.03em;
}
</style>
