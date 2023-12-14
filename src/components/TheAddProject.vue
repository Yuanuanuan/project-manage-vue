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
          v-model="title"
          placeholder="Enter the project name"
        />
      </div>
      <div class="input-box">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          v-model="description"
          placeholder="Enter description about the project"
        ></textarea>
      </div>
      <div class="input-box">
        <label for="dead-line">Dead Line</label>
        <input type="date" id="dead-line" name="dead-line" v-model="date" />
      </div>
      <div v-if="!isInputValid" class="error-msg">
        Please make sure you're enter the all field.
      </div>
      <div class="button-box">
        <BaseButton type="button" @click="handleCancel">Cancel</BaseButton>
        <BaseButton type="submit">Submit</BaseButton>
      </div>
    </form>
  </div>
</template>

<!-- Options API -->
<!-- <script>
export default {
  props: {
    isValid: {
      type: Boolean,
      default: true,
    },
  },
  emits: ["push", "cancel"],
  data() {
    return {
      isInputValid: true,
    };
  },
  methods: {
    getRandomNum() {
      return (Math.random() * 100).toFixed(3);
    },
    handleCancel() {
      this.isInputValid = true;
      this.$emit("cancel");
    },
    handleSubmit() {
      const time = new Date();
      const day = time.getDate();
      const month = time.getMonth() + 1;
      const year = time.getFullYear();
      const beginning = `${year}-${month}-${day}`;

      const newProject = {
        id: this.getRandomNum(),
        title: this.$refs.title.value,
        description: this.$refs.description.value,
        beginning,
        date: this.$refs.date.value,
      };

      if (
        !newProject.title.trim() ||
        !newProject.description.trim() ||
        !newProject.date.trim()
      ) {
        this.isInputValid = false;
        return;
      }
      this.isInputValid = true;
      this.$refs.title.value = "";
      this.$refs.description.value = "";
      this.$refs.date.value = "";

      this.$emit("push", newProject);
    },
  },
};
</script> -->

<!-- Composition API -->
<script>
import { ref } from "vue";

export default {
  emits: ["push", "cancel"],
  setup(props, ctx) {
    const isInputValid = ref(true);
    const title = ref("");
    const description = ref("");
    const date = ref("");

    function getRandomNum() {
      return (Math.random() * 100).toFixed(3);
    }

    function handleCancel() {
      isInputValid.value = true;
      ctx.emit("cancel");
    }

    function handleSubmit() {
      const time = new Date();
      const day = time.getDate();
      const month = time.getMonth() + 1;
      const year = time.getFullYear();
      const beginning = `${year}-${month}-${day}`;

      const newProject = {
        id: getRandomNum(),
        title: title.value,
        description: description.value,
        beginning,
        date: date.value,
      };

      if (
        !newProject.title.trim() ||
        !newProject.description.trim() ||
        !newProject.date.trim()
      ) {
        isInputValid.value = false;
        return;
      }
      isInputValid.value = true;
      title.value = "";
      description.value = "";
      date.value = "";

      ctx.emit("push", newProject);
    }

    return {
      title,
      description,
      date,
      isInputValid,
      handleCancel,
      handleSubmit,
    };
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

.error-msg {
  margin: 1rem 0;
  font-size: 1.05rem;
  font-weight: 500;
  color: red;
  font-style: italic;
  animation: shake 0.2s ease-in-out 2;
}

@keyframes shake {
  0% {
    margin-left: 0rem;
  }
  25% {
    margin-left: 0.25rem;
  }
  75% {
    margin-left: -0.25rem;
  }
  100% {
    margin-left: 0rem;
  }
}
</style>
