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

<script>
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
  data() {
    return {
      projectsData: [
        {
          id: "1",
          title: "Learn Vue",
          description: "Just need to learn Vue",
          beginning: "2023-12-1",
          date: "2023-12-31",
        },
      ],
      projectId: null,
      isAdd: false,
    };
  },
  methods: {
    getRandomNum() {
      return (Math.random() * 100).toFixed(3);
    },
    handleAddProject() {
      this.isAdd = true;
      this.projectId = null;
    },
    handleCancelAdd() {
      this.isAdd = false;
    },
    pushProjectData(data) {
      this.projectId = data.id;
      this.projectsData.unshift(data);
      this.isAdd = false;
    },
    deleteProject(id) {
      this.projectsData = this.projectsData.filter(
        (project) => project.id !== id
      );
    },
  },
  computed: {
    currentProject() {
      return this.projectsData.find((item) => item.id === this.projectId);
    },
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
