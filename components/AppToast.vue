<template>
  <div class="toast">
    <slot></slot>
  </div>
</template>

<script>
  export default {

  }
</script>

<style lang="scss" scoped>
.toast {
  position: absolute;
  top: 0;
  right: 0;
  padding: 12px 24px;
  border-radius: 3px;
  background: #a8060e;
  text-align: center;
  color: white;

  a {
    text-decoration: none;
    font-weight: bold;
    color: white;
  }
}
</style>
