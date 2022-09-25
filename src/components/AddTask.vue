<template>
  <div>
    <div class="row">
      <input
        @change="getToDoText"
        :value="todoText"
        class="col form-control mr-2"
        type="text"
        placeholder="Insert your task here"
      />
      <button @click="addTask" class="btn btn-primary">Add Task</button>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";
import { v1 } from "uuid";

export default {
  data() {
    return {
      todoText: ""
    };
  },
  methods: {
    ...mapActions(["addTodo"]),
    getToDoText(e) {
      this.todoText = e.target.value;
    },

    addTask() {
      this.addTodo({
        id: v1(),
        title: this.todoText,
        complete: false
      });
      this.todoText = "";
    }
  }
};
</script>
