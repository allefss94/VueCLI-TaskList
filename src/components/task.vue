<template>
  <div @click="$emit('TaskChange', task)" class="task" :class="stateClass">
      <span @click.stop="$emit('removeTask', task)" class="close">x</span>
      <p>{{ task.name }}</p>
  </div>
</template>

<script>
export default {
    props:{
        task: {type: Object, required: true}  
    },  
    computed:{
        stateClass(){
            return {
                pending: this.task.pending,
                done: !this.task.pending
            }
        }
    },
}
</script>

<style>
    .task{
        position: relative;
        box-sizing: border-box;
        width: 350px;
        height: 150px;
        padding: 10px;
        border-radius: 8px;
        font-weight: 300;
        font-size: 2rem;
        cursor: pointer;
        user-select: none;
        display: flex;
        justify-content: center;
        align-items: center;
        margin: 15px;
    }
    .pending{
        border-left: 12px solid #cc1111;
        background-color: #e42121;
    }
    .done{
        border-left: 12px solid #08a368;
        background-color: #13b375;
        color: #DDD;
        text-decoration: line-through;
    }
    .pending .close{
        background-color: #ad0e0e;
    }
    .done .close{
        background-color: #088857;
    }
    .close{
        position: absolute;
        top: 10px;
        right: 10px;
        padding-bottom: 5px;
        width: 20px;
        height: 20px;
        border-radius: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 0.9rem;
        font-weight: 600;
    }
</style>