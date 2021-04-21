<template>
  <div>
    <label for="thing">Which is your favorite {{ cuisine }}?</label>
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
