<template>
  <div>
    <pre>{{ $data }}</pre>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  data() {
    return {
      id: this.$route.params.id
    };
  },
  computed: {
    ...mapState(["fooddata"]),
    currentItem() {

    }
  }
};
</script>

<style lang="scss" scoped></style>
