<template>
  <div class="new-task">
    <input @keypress.enter="add" v-model="name" type="text" />
    <button @click="add">+</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: ""
    };
  },
  methods: {
    add() {
      if (this.name.length > 0) {
        this.$emit("addTask", { name: this.name, pending: true });
        this.name = "";
      }
    }
  }
};
</script>

<style>
.new-task {
  display: flex;
  justify-content: center;
  margin: 25px;
}
.new-task input {
  padding: 8px;
  border: none;
  border-radius: 5px 0px 0px 5px;
  width: 250px;
  opacity: 0.4;
}
.new-task button {
  border-radius: 0px 5px 5px 0px;
  border: none;
  padding: 0px 20px;
  background-color: rgb(24, 141, 141);
  color: #fff;
}
</style>