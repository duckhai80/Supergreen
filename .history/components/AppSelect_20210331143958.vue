<template>
  <div>
    <label :for="select">What {{ select }} do you want?</label>
    <select :name="select" :id="select">
      <option value="">-- Please select a {{ select }}</option>
      <option value="">firstthing</option>
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
    selectOptions: {
      type: Array,
      default: () => ['tacos', 'pizza', 'dim sum'];
    }
  },
};
</script>

<style lang="scss" scoped></style>
