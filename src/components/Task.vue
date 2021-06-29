<template>
  <div
    @click="$emit('taskStateChanged', task)"
    class="task"
    :class="stateClass"
  >
    <span @click.stop="$emit('taskDeleted', task)" class="close">x</span>
    <p>{{ task.name }}</p>
  </div>
</template>

<script>
export default {
  props: {
    task: { type: Object, required: true },
  },
  computed: {
    stateClass() {
      return {
        pending: this.task.pending,
        done: !this.task.pending,
      };
    },
  },
};
</script>

<style>
.task {
  box-sizing: border-box;
  position: relative;
  width: 350px;
  height: 150px;
  padding: 10px;
  border-radius: 8px;
  font-size: 2rem;
  font-weight: 300;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
}

.pending {
  border-left: 12px solid rgb(143, 0, 143);
  background-color: rgb(202, 0, 202);
}

.done {
  border-left: 12px solid rgb(82, 0, 82);
  background-color: purple;
  text-decoration: line-through;
}

.close {
  background-color: black;
  position: absolute;
  top: 10px;
  right: 10px;
  border-radius: 8px;
  font-size: 0.9rem;
  font-weight: 600;
  height: 20px;
  width: 20px;
  border-radius: 10px;
  display: flex;
  justify-content: center;
}
</style>