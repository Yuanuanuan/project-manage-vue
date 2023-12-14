<template>
  <div class="container">
    <div>
      <h1>Your Projects</h1>
      <button @click="$emit('add')">+ Add Projects</button>
      <ul>
        <li
          v-for="item in data"
          :key="item.id"
          :class="{ active: projectId === item.id }"
          @click="handleCloseAddForms(item.id)"
        >
          {{ item.title }}
          <img :src="imgUrl" @click="$emit('delete', item.id)" />
        </li>
      </ul>
    </div>
  </div>
</template>

<!-- Options API -->
<!-- <script setup>
import { ref, computed } from "vue";
import trashIcon from "../../assets/trash-icon.svg";

const props = defineProps({
  data: Array,
  modelValue: String,
  currentProject: Object,
});

const emit = defineEmits(["close", "add", "delete", "update:modelValue"]);

const imgUrl = ref(trashIcon);

function handleCloseAddForms(id) {
  emit("close");
  projectId.value = id;
}

const projectId = computed({
  get() {
    return props.modelValue;
  },
  set(id) {
    emit("update:modelValue", id);
  },
});
</script> -->

<!-- Composition API -->
<script setup>
import { ref, computed } from "vue";
import trashIcon from "../../assets/trash-icon.svg";

const props = defineProps({
  data: Array,
  modelValue: String,
  currentProject: Object,
});

const emits = defineEmits(["close", "add", "delete", "update:modelValue"]);

const imgUrl = ref(trashIcon);

function handleCloseAddForms(id) {
  emits("close");
  projectId.value = id;
}

const projectId = computed({
  get() {
    return props.modelValue;
  },
  set(id) {
    emits("update:modelValue", id);
  },
});
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
  max-height: 75vh;
  overflow-y: scroll;
}

ul::-webkit-scrollbar {
  display: none;
}

li {
  width: 100%;
  padding: 1rem;
  margin-top: 1rem;
  border-radius: 12px;
  color: #e8e8e8;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
}

li:hover {
  background-color: #e8e8e870;
}

li:hover img {
  display: block;
}

li.active {
  border: 2px solid #e8e8e8;
  padding: calc(1rem - 2px);
}

img {
  height: 24px;
  display: none;
}

img:hover {
  filter: drop-shadow(0 0 5px #ffffff);
}
</style>
