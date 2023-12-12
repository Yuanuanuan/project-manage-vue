<template>
  <div class="container">
    <div class="card">
      {{ console.log(currentProject) }}
      <!-- <h1>{{ currentProject.title }}</h1>
      <h2>{{ currentProject.description }}</h2>
      <h3>{{ currentProject.date }}</h3> -->
    </div>
  </div>
</template>

<script>
export default {
  inject: ["currentProject"],
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
