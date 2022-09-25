<template>
  <div id="app" class="container">
    <div id="title" class="mb-2">
      TASK LIST
    </div>
    <AddTask />
    <TasksStatus />
    <TodoList />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList";
import TasksStatus from "@/components/TasksStatus";
import AddTask from "@/components/AddTask";

export default {
  name: "App",
  components: {
    AddTask,
    TodoList,
    TasksStatus
  }
};
</script>

<style>
#app {

  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#title {
  color: blue;
  font-size: large;
}
</style>
