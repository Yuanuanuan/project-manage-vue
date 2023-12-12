<template>
  <main>
    <TheSideBar
      :data="projectsData"
      @add="handleAddProject"
      @getProject="getProjectDetails"
    />
    <keep-alive>
      <TheProject v-if="isAdd === false" :data="currentProject"></TheProject>
      <TheAddProject
        v-else-if="isAdd === true"
        @push="pushProjectData"
        @cancel="handleCancelAdd"
      ></TheAddProject>
    </keep-alive>
  </main>
</template>

<script>
import TheSideBar from "./components/layouts/TheSideBar.vue";
import TheAddProject from "./components/TheAddProject.vue";
import TheProject from "./components/TheProject.vue";

export default {
  components: {
    TheSideBar,
    TheProject,
    TheAddProject,
  },
  data() {
    return {
      projectsData: [
        {
          id: "1",
          title: "Learn Vue",
          description: "Just need to learn Vue",
          date: "2023-12-31",
        },
      ],
      currentProject: null,
      isAdd: false,
    };
  },
  methods: {
    getProjectDetails(id) {
      return (this.currentProject = this.projectsData.find(
        (project) => project.id === id
      ));
    },
    getRandomNum() {
      return (Math.random() * 100).toFixed(3);
    },
    handleAddProject() {
      this.isAdd = true;
    },
    handleCancelAdd() {
      this.isAdd = false;
    },
    pushProjectData(data) {
      if (
        data.title.trim() === "" ||
        data.description.trim() === "" ||
        data.date.trim() === ""
      ) {
        return;
      }
      this.projectsData.unshift(data);
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
