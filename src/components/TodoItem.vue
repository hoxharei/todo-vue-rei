<template>
  <div>

    <div  class="row my-3 justify-content-between align-items-center">
      <div>
        <input :checked="todo.complete" class="mr-1" @change="onCompleted" type="checkbox" v-if="!todo.complete"/>
        <label :style="{'color':textColor}">{{todo.complete ? 'Completed' : 'Complete'}}</label>
      </div>
      <h3 v-if="!editing">{{todo.title}}</h3>
      <div v-else class="mr-2 row justify-content-between align-items-center col">
        <input
          v-bind:value="todoText"
          @change="todoTextChange"
          type="text"
          class="col-7 form-control"
        />
      </div>
      <div class="row align-items-center">
        <button @click="updateTodoI(todo)" class="btn btn-primary mx-2">{{editing?'Update':'Edit'}}</button>
        <button @click="deleteTodo(todo.id)" class="btn btn-danger">Delete</button>
      </div>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex";
export default {
  props: {
    todo: {}
  },
  data() {
    return {
      todoText: "",
      editing: false,
      completed: false,
      textColor: this.todo.complete ? 'green' : 'red'
    };
  },
  methods: {
    ...mapActions(["deleteTodo", "updateTodo", "changeCompleted"]),
    onCompleted() {
      this.todo.complete = !this.todo.complete
      this.textColor = "green"
      this.updateTodo(this.todo)
      this.changeCompleted()

    },
    todoTextChange(e) {
      this.todoText = e.target.value;
    },
    updateTodoI(todo) {
      this.editing = this.editing == true ? false : true;
      if (this.editing) {
        this.todoText = todo.title;
        this.updateTodo(todo);
      } else {
        todo.title = this.todoText;
      }
    }
  }
};
</script>

<style scoped>
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
</style>