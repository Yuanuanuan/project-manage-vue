<template>
  <div class="container">
    <div class="card" v-if="data">
      <h1>{{ data.title }}</h1>
      <h2>{{ data.description }}</h2>
      <h3>{{ data.date }}</h3>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: Object,
  },
};
</script>

<style scoped>
.container {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.card {
  width: 60vw;
  height: 80vh;
  padding: 1.5rem;
}
</style>
