<template>
  <main>
    <TheSideBar
      v-model="projectId"
      :data="projectsData"
      @close="handleCancelAdd"
      @add="handleAddProject"
      @delete="deleteProject"
    />
    <keep-alive>
      <TheProject
        v-if="isAdd === false && currentProject"
        :data="currentProject"
      ></TheProject>
      <TheAddProject
        v-else-if="isAdd === true"
        @push="pushProjectData"
        @cancel="handleCancelAdd"
      ></TheAddProject>
      <TheNoProject v-else></TheNoProject>
    </keep-alive>
  </main>
</template>

<!-- Options API -->
<!-- <script>
import { ref, computed } from "vue";
import TheSideBar from "./components/layouts/TheSideBar.vue";
import TheAddProject from "./components/TheAddProject.vue";
import TheProject from "./components/TheProject.vue";
import TheNoProject from "./components/TheNoProject.vue";

export default {
  components: {
    TheSideBar,
    TheProject,
    TheAddProject,
    TheNoProject,
  },
  setup() {
    const projectsData = ref([
      {
        id: "1",
        title: "Learn Vue",
        description: "Just need to learn Vue",
        beginning: "2023-12-1",
        date: "2023-12-31",
      },
    ]);
    const projectId = ref(null);
    const isAdd = ref(false);

    const currentProject = computed(() => {
      return projectsData.value.find((item) => item.id === projectId.value);
    });

    function getRandomNum() {
      return (Math.random() * 100).toFixed(3);
    }

    function handleAddProject() {
      isAdd.value = true;
      projectId.value = null;
    }

    function handleCancelAdd() {
      isAdd.value = false;
    }

    function pushProjectData(data) {
      projectId.value = data.id;
      projectsData.value.unshift(data);
      isAdd.value = false;
    }

    function deleteProject(id) {
      projectsData.value = projectsData.value.filter(
        (project) => project.id !== id
      );
    }

    return {
      projectsData,
      projectId,
      isAdd,
      getRandomNum,
      handleAddProject,
      handleCancelAdd,
      pushProjectData,
      deleteProject,
      currentProject,
    };
  },
};
</script> -->

<!-- Composition API -->
<script>
import { ref, computed } from "vue";
import TheSideBar from "./components/layouts/TheSideBar.vue";
import TheAddProject from "./components/TheAddProject.vue";
import TheProject from "./components/TheProject.vue";
import TheNoProject from "./components/TheNoProject.vue";

export default {
  components: {
    TheSideBar,
    TheProject,
    TheAddProject,
    TheNoProject,
  },
  setup() {
    const projectsData = ref([
      {
        id: "1",
        title: "Learn Vue",
        description: "Just need to learn Vue",
        beginning: "2023-12-1",
        date: "2023-12-31",
      },
    ]);
    const projectId = ref(null);
    const isAdd = ref(false);

    const currentProject = computed(() => {
      return projectsData.value.find((item) => item.id === projectId.value);
    });

    function getRandomNum() {
      return (Math.random() * 100).toFixed(3);
    }

    function handleAddProject() {
      isAdd.value = true;
      projectId.value = null;
    }

    function handleCancelAdd() {
      isAdd.value = false;
    }

    function pushProjectData(data) {
      projectId.value = data.id;
      projectsData.value.unshift(data);
      isAdd.value = false;
    }

    function deleteProject(id) {
      projectsData.value = projectsData.value.filter(
        (project) => project.id !== id
      );
    }

    return {
      projectsData,
      projectId,
      isAdd,
      getRandomNum,
      handleAddProject,
      handleCancelAdd,
      pushProjectData,
      deleteProject,
      currentProject,
    };
  },
};
</script>

<style scoped>
main {
  width: 100vw;
  height: 100vh;
  display: flex;
}
</style>
