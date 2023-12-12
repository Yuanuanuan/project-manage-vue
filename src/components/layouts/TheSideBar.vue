<template>
  <div class="container">
    <div>
      <h1>Your Projects</h1>
      <button @click="this.$emit('add')">+ Add Projects</button>
      <ul>
        <li
          v-for="item in data"
          :key="item.id"
          @click="this.$emit('getProject', item.id)"
        >
          {{ item.title }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: ["data"],
  emits: ["add", "getProject"],
};
</script>

<style scoped>
.container {
  padding: 3rem;
  height: 100vh;
  width: 350px;
  border-radius: 0 30px 30px 0;
  background-color: #333;
  color: #fff;
}

button {
  margin-top: 1rem;
  padding: 0.5rem 0.8rem;
  background-color: #444444;
  border: 2px solid #e8e8e8;
  color: #e8e8e8;
  border-radius: 10px;
  font-size: 1.05rem;
  cursor: pointer;
}

button:hover {
  box-shadow: 0 0 10px #e9e9e9;
  text-shadow: 0 0 10px #e9e9e9;
}

ul {
  list-style: none;
}

li {
  width: 100%;
  padding: 1rem;
  margin-top: 1rem;
  border-radius: 12px;
  color: #e8e8e8;
  cursor: pointer;
}

li:hover {
  background-color: #e8e8e870;
}

li.active {
  border: 2px solid #e8e8e8;
}
</style>
