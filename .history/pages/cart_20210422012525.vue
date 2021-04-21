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
    <!-- <AppCheckout v-if="cart.length"></AppCheckout> -->

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

import { StripeElements, StripeElement } from "vue-stripe-elements-plus";

import { mapState, mapGetters } from "vuex";

export default {
  components: {
    AppCheckout,
    AppEmptyCart,
    StripeElements,
    StripeElement
  },
  computed: {
    ...mapState(["cart"]),
    ...mapGetters(["totalPrice"])
  },
  data() {
    return {
      stripeKey: "pk_test_TYooMQauvdEDq54NiTphI7jx", // test key, don't hardcode
      instanceOptions: {
        // https://stripe.com/docs/js/initializing#init_stripe_js-options
      },
      elementsOptions: {
        // https://stripe.com/docs/js/elements_object/create#stripe_elements-options
      },
      cardOptions: {
        // reactive
        // remember about Vue 2 reactivity limitations when dealing with options
        value: {
          postalCode: ""
        }
        // https://stripe.com/docs/stripe.js#element-options
      }
    };
  },

  methods: {
    pay() {
      // ref in template
      const groupComponent = this.$refs.elms;
      const cardComponent = this.$refs.card;
      // Get stripe element
      const cardElement = cardComponent.stripeElement;

      // Access instance methods, e.g. createToken()
      groupComponent.instance.createToken(cardElement).then(result => {
        // Handle result.error or result.token
      });
    }
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

.payment-simple {
  padding: 20px;
  width: 600px;

  button {
    font-size: 18px;
    // height: 32px;
  }
}
</style>
