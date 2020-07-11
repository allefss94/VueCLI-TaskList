<template>
  <div id="app">
    <h1>Tarefas</h1>
    <task-progress :progress="progress" />
    <newTask @addTask="addTask($event)" />

    <taskGrid @removeTask="removeTask" @TaskChange="toggleStateTask" :tasks="tasks" />
  </div>
</template>

<script>
import TaskProgress from "./components/taskProgress.vue";
import taskGrid from "./components/taskGrid.vue";
import newTask from "./components/newTask.vue";
export default {
  components: { taskGrid, newTask, TaskProgress },
  data() {
    return {
      tasks: []
    };
  },
  methods: {
    addTask(newtask) {
      const sameName = t => t.name === newtask.name;
      const reallyNew = this.tasks.filter(sameName).length == 0;
      if (reallyNew) {
        this.tasks.push(newtask);
      } else {
        alert("o Nome ja foi utilizado");
      }
    },
    removeTask(i) {
      this.tasks.splice(i, 1);
    },
    toggleStateTask(i) {
      this.tasks[i].pending = !this.tasks[i].pending;
    }
  },
  computed: {
    progress() {
      const total = this.tasks.length;
      const done = this.tasks.filter(t => !t.pending).length;
      return Math.round((done / total) * 100) || 0;
    }
  },
  watch: {
    tasks: {
      deep: true,
      handler() {
        localStorage.setItem("tasks", JSON.stringify(this.tasks));
      }
    }
  },
  created() {
    const json = localStorage.getItem("tasks");
    this.tasks = JSON.parse(json) || [];
  }
};
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
  color: #fff;
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
</style>
