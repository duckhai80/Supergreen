<template>
  <div>
    <label :for="thing">What {{ cuisine }} do you want?</label>
    <select name="thing" id="thing">
      <option value="firstthing">firstthing</option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    select: {
      type: String,
      default: "cuisine"
    },
  },
};
</script>

<style lang="scss" scoped></style>
