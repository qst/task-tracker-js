<template>
  <div :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>
      {{ task.text }}
      <i @click="onDelete(task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>



<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {
    onDelete(id) {
      console.log("Debug " + id + " in Task.vue");
      this.$emit("delete-task", id);
    },
  },
  emits: ["delete-task"],
};
</script>

<style scoped>
.fas {
  color: red;
}
.task {
  background: #f1f1f1;
  margin: 0.4em;
  padding: 0.7em;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}

.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>