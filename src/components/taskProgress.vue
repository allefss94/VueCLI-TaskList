<template>
  <div class="tasks-progress">
    <span class="progress-value">{{progress}}%</span>
    <div class="progress-bar" :style="{width: progress +'%'}"></div>
  </div>
</template>

<script>
export default {
  props: {
    progress: { type: Number, default: 0 }
  }
};
</script>

<style>
.tasks-progress {
  position: relative;
  width: 50%;
  border: 1px solid #fff;
  border-radius: 4px;
  margin-bottom: 15px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.progress-bar {
  position: absolute;
  background-color: rgb(73, 131, 77);
  height: 100%;
  border-radius: 4px;
  transition: all 500ms;
  align-self: flex-start;
}
.progress-value {
  z-index: 1;
  font-size: 1.5rem;
}
</style>