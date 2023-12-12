<template>
  <div class="container">
    <h1>Add New Project</h1>
    <form @submit.prevent="handleSubmit">
      <div class="input-box">
        <label for="title">Title</label>
        <input
          type="text"
          id="title"
          name="title"
          ref="title"
          placeholder="Enter the project name"
          required
        />
      </div>
      <div class="input-box">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          ref="description"
          placeholder="Enter description about the project"
          required
        ></textarea>
      </div>
      <div class="input-box">
        <label for="dead-line">Dead Line</label>
        <input
          type="date"
          id="dead-line"
          name="dead-line"
          ref="date"
          required
        />
      </div>
      <div class="button-box">
        <BaseButton type="button" @click="$emit('cancel')"
          >Cancel</BaseButton
        >
        <BaseButton type="submit">Submit</BaseButton>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: [""],
  emits: ["push", "cancel"],
  methods: {
    getRandomNum() {
      return (Math.random() * 100).toFixed(3);
    },
    handleSubmit() {
      const newProject = {
        id: this.getRandomNum(),
        title: this.$refs.title.value,
        description: this.$refs.description.value,
        date: this.$refs.date.value,
      };

      this.$emit("push", newProject);

      this.$refs.title.value = "";
      this.$refs.description.value = "";
      this.$refs.date.value = "";
    },
  },
};
</script>

<style scoped>
.container {
  flex: 1;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
  font-family: "Lora", serif;
}
.button-box {
  display: flex;
  gap: 10px;
  position: absolute;
  bottom: 2rem;
  right: 2rem;
}

h1 {
  margin-top: 5rem;
  font-family: "Lora", serif;
  color: #222;
}

form {
  max-width: 600px;
  width: 75%;
  height: 70%;
  margin-top: 2rem;
  padding: 3rem;
  border-radius: 24px;
  box-shadow: 5px 5px 10px #999999;
  position: relative;
}

.input-box {
  width: 100%;
  font-family: "Lora", serif;
}

.input-box label {
  display: block;
  font-size: 1.25rem;
  margin: 0.8rem 0;
  font-family: "Lora", serif;
}

.input-box input {
  outline: none;
  padding: 0.5rem;
  width: 100%;
  height: 40px;
  font-size: 1.15rem;
  font-family: "Lora", serif;
}

input::placeholder,
textarea::placeholder {
  font-family: "Lora", serif;
}

.input-box textarea {
  outline: none;
  padding: 0.5rem;
  width: 100%;
  height: 120px;
  font-size: 1.15rem;
  font-family: "Lora", serif;
  resize: none;
}
</style>
