<template>
  <main class="container cart">
    <h2>Cart</h2>
    <section v-if="cart.length">
      <table>
        <thead>
          <tr>
            <th>Item</th>
            <th>Add Ons</th>
            <th>Amount</th>
            <th>Total Price</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in cart" :key="item.id">
            <td>
              {{ item.item }}
              <span v-if="item.options">- {{ item.options }}</span>
            </td>
            <td>
              <span v-for="addon in item.addOns" :key="addon" class="comma">
                {{ addon }}
              </span>
            </td>
            <td>{{ item.count }}</td>
            <td>{{ item.combinedPrice }}</td>
          </tr>
          <tr>
            <td colspan="3"></td>
            <td class="total">Total: ${{ totalPrice.toFixed(2) }}</td>
          </tr>
        </tbody>
      </table>
    </section>
    <AppEmptyCart v-else></AppEmptyCart>
    <AppCheckout v-if="cart.length"></AppCheckout>
    <div class="payment-simple">
      <StripeElements
        :stripe-key="stripeKey"
        :instance-options="instanceOptions"
        :elements-options="elementsOptions"
        #default="{ elements }"
        ref="elms"
      >
        <StripeElement
          type="card"
          :elements="elements"
          :options="cardOptions"
          ref="card"
        />
      </StripeElements>
      <button @click="pay" type="button">Pay</button>
    </div>
  </main>
</template>

<script>
import AppCheckout from "@/components/AppCheckout.vue";
import AppEmptyCart from "@/components/AppEmptyCart.vue";

import { mapState, mapGetters } from "vuex";

export default {
  components: {
    AppCheckout,
    AppEmptyCart
  },
  computed: {
    ...mapState(["cart"]),
    ...mapGetters(["totalPrice"])
  }
};
</script>

<style lang="scss" scoped>
.cart.container {
  margin: 0 auto;
  padding: 100px;
  max-width: 1000px;

  h2 {
    text-align: center;
  }

  .total {
    font-weight: bold;
  }
}
</style>
