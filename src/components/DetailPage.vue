<template>
  <div class="containers">
    <h1>{{ title }}</h1>
  </div>
</template>

<script>
export default {
  name: "Detail-page",
  props: {
    title: {
      type: String,
      default: "Detail Page",
    },
  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style scoped>
h1 {
  display: flex;
  text-align: center;
  justify-content: center;
  align-items: center;
  margin-bottom: 3rem;
}
</style>
