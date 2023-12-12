<template>
  <button :type="type" :mode="mode">
    <slot>Button</slot>
  </button>
</template>

<script>
export default {
  props: ["type", "mode"],
};
</script>

<style scoped>
button {
  padding: 0.75rem 1.25rem;
  font-family: inherit;
  font-size: 1.05rem;
  background-color: #333;
  border: none;
  border-radius: 8px;
  color: #fff;
  cursor: pointer;
  position: relative;
  z-index: 1;
  transition: color 0.5s ease-in-out;
}

button::after {
  content: "";
  width: 0%;
  height: 100%;
  background-color: #fff;
  position: absolute;
  top: 0;
  left: 0;
  transition: width 0.5s ease-in-out;
  z-index: -1;
}

button:hover::after {
  width: 100%;
}

button:hover {
  color: #333;
}
</style>
