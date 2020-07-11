<template>
  <div class="taskGrid">
    <template v-if="tasks.length">
      <Task
        class="task"
        v-for="(task, i) in tasks"
        :key="task.name"
        :task="task"
        @removeTask="$emit('removeTask', i)"
        @TaskChange="$emit('TaskChange', i)"
      />
    </template>
    <p v-else class="no-task">Sua vida está em dias :)</p>
  </div>
</template>

<script>
import Task from "./task.vue";
export default {
  components: { Task },
  props: {
    tasks: { type: Array }
  }
};
</script>

<style>
.taskGrid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: flex-end;
}
.taskGrid .task {
  margin: 10px;
}
.no-task {
  color: #fff;
  font-size: 1.7rem;
}
</style>