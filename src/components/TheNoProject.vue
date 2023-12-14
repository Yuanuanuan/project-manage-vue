<template>
  <div class="container">
    <section>
      <img :src="imgUrl" />
      <h1>You can add New Project in the sidebar on there of left!</h1>
    </section>
  </div>
</template>

<!-- Options API -->
<!-- <script>
export default {
  data() {
    return {
      imgUrl:
        "https://github.com/Yuanuanuan/project-management/blob/main/public/logo.png?raw=true",
    };
  },
};
</script> -->

<!-- Composition API -->
<script setup>
import { ref } from "vue";

const imgUrl = ref(
  "https://github.com/Yuanuanuan/project-management/blob/main/public/logo.png?raw=true"
);
</script>

<style scoped>
.container {
  flex: 1;
  display: flex;
  justify-content: center;
}

section {
  margin-top: 6rem;
  max-width: 600px;
  height: 70vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}

img {
  width: 100px;
  margin-bottom: 2rem;
}

h1 {
  font-size: 1.25rem;
}
</style>
