<template>
  <nav>
    <ul>
      <li>
        <nuxt-link exact="" to="/"><AppLogo></AppLogo></nuxt-link>
      </li>
      <li><nuxt-link to="/restaurants">Restaurants</nuxt-link></li>
    </ul>
    <div v-if="cartCount > 0" class="smallnum">{{ cartCount }}</div>
    <nuxt-link to="/cart">Cart</nuxt-link>
  </nav>
</template>

<script>
import AppLogo from "@/components/AppLogo.vue";
import { mapGetters } from "vuex";

export default {
  components: {
    AppLogo
  },
  computed: {
    ...mapGetters(["cartCount"])
  }
};
</script>

<style lang="scss" scoped>
.smallnum {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 9px;
  padding: 6px 10px;
  right: 33px;
  width: 25px;
  height: 25px;
  background: white;
  border-radius: 1000px;
  text-align: center;
  color: black;
  font-size: 10px;
  font-weight: bold;
}
</style>
