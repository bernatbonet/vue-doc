<template>
  <div id="app">
    <h1 class="ui dividing centered header">Vue.js Todo App</h1>
    <div class='ui three column centered grid'>
      <div class='column'>
        <todo-list v-bind:todos="todos"></todo-list>
        <create-todo v-on:create-todo="addTodo"></create-todo>
      </div>
    </div>
  </div>
</template>

<script>
import Message from './components/Message.vue';
import TodoList from './components/TodoList.vue';
import CreateTodo from './components/CreateTodo.vue';
export default {
  name: 'app',
  components: { Message, TodoList, CreateTodo, },
  data () {
    return {
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false,
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true,
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false,
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false,
      }]
    }
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push(newTodo);
      //sweetalert('Success!', 'To-Do created!', 'success');
    },
  },
}
</script>

<style>

</style>
