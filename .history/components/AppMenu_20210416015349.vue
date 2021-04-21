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
  text-align: center;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 9px;
  right: 33px;
  padding: 6px 10px;
  width: 25px;
  height: 25px;
  border-radius: 1000px;
  background: white;
  font-size: 10px;
  font-weight: bold;
  color: black;
}
</style>
