<template>
  <div>
    <section class="masthead" role="img" aria-label="Image Description">
      <h1>
        Supergreen
      </h1>
      <button>
        See restaurants
      </button>
    </section>
  </div>
</template>

<script>
export default {
  setup() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
.masthead {
  padding: 40px;
  width: 100%;
  height: 96vh;
  background-size: cover !important;
  background: radial-gradient(
      ellipse at center,
      rgba(0, 0, 0, 0) 0%,
      rgba(0, 0, 0, 0) 37%,
      rgba(0, 0, 0, 0.65) 100%
    ),
    url(~assets/headerimg.jpg) no-repeat center center scroll;
  overflow: hidden;
}

h1 {
  margin-bottom: 40px;
  line-height: 1;
  text-shadow: 1px 2px 4px rgba(0, 0, 0, 0.8);
  font-style: normal;
  font-size: 8vmin;
  font-weight: bold;
  color: #eee;
  letter-spacing: 0.03em;
}
</style>
