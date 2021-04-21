<template>
  <div>
    <pre>{{ $data }}</pre>
  </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
  computed: {
    ...mapState([
      'nameOfState',
    ])
  },
  data() {
    return {
      id: this.$route.params.id
    };
  }
};
</script>

<style lang="scss" scoped></style>
