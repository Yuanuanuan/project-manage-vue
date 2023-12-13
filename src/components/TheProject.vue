<template>
  <div class="container">
    <div class="card">
      <h1>{{ data.title }}</h1>
      <h3>About Project</h3>
      <p class="textarea">{{ data.description }}</p>
      <h3>During time of project</h3>
      <p>{{ data.begining }} - {{ data.date }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: {
      type: Object,
      required: true,
    },
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

h1 {
  font-size: 3.5rem;
  font-weight: 600;
  margin: 2rem 0;
}

h3 {
  font-size: 2rem;
  margin: 1rem 0;
}

.textarea {
  height: 250px;
  padding: 1rem;
  background-color: #f0f0f0;
  border-radius: 12px;
}

p {
  font-size: 1.15rem;
  height: 60px;
  background-color: #f0f0f0;
  border-radius: 12px;
  padding: 1rem;
}
</style>
