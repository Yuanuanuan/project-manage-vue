<template>
  <main>
    <TheSideBar
      :data="projectsData"
      @setIsAdd="handleCancelAdd"
      @add="handleAddProject"
      v-model="projectId"
    />
    <keep-alive>
      <TheNoProject v-if="currentProject === undefined"></TheNoProject>
      <TheProject
        v-else-if="isAdd === false"
        :data="currentProject"
      ></TheProject>
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
          date: "2023-12-31",
        },
      ],
      projectId: null,

      // null === NoProject
      // true === Adding Project
      // false === Watching Project
      isAdd: null,
    };
  },
  methods: {
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
      if (!data.title.trim() || !data.description.trim() || !data.date.trim()) {
        return;
      }
      this.projectsData.unshift(data);
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
