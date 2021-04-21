<template>
  <main class="container cart">
    <h2>Cart</h2>
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
        <tr>
          <td>Quesadilla
            <span>- Plain</span>
          </td>
          <td><span class="comma">none</span></td>
          <td>1</td>
          <td>7.00</td>
        </tr>
        <tr>
          <td colspan="3"></td>
          <td class="total">Total: $14.00</td>
        </tr>
      </tbody>
    </table>
  </main>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped></style>
