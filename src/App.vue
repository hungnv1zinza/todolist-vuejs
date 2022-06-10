<template>
  <div class="h-100 w-full flex items-center justify-center bg-teal-lightest font-sans">
    <div class="bg-white rounded shadow p-6 m-4 w-full lg:w-1/2 lg:max-w-3/4">
      <component
          :tasks="tasksFiltered"
          :is="currentComponent"
          @createTodo="handleCreateTodo"
          @doneTodo="handleDoneTodo"
          @deleteTodo="handleDeleteTodo"
          @search="handleSearch"
          @changePage="handleChangePage"
      />
    </div>
  </div>
</template>

<script>
import TodoList from './components/Todo/TodoList.vue'
import TodoCreate from './components/Todo/TodoCreate.vue'

export default {
  name: 'App',
  components: {
    'TodoList': TodoList,
    'TodoCreate': TodoCreate
  },
  data() {
    return {
      currentComponent: "TodoList",
      tasks: [
        {name: 'Task 1', done: false},
        {name: 'Task 2', done: false},
        {name: 'Task 3', done: false},
        {name: 'Task 4', done: false},
      ],
      search: ''
    }
  },
  computed: {
    tasksFiltered() {
      if (this.search.length) {
        return this.tasks.filter(data => data.name.toLowerCase().includes(this.search.toLowerCase()))
      } else {
        return this.tasks;
      }
    }
  },
  methods: {
    /**
     *
     * @param {KeyboardEvent} e
     */
    handleSearch(e) {
      this.search = e.target.value
    },
    handleCreateTodo(payload) {
      this.tasks.push({
        ...payload
      })
      this.currentComponent = 'TodoList'
      this.search = '';
    },
    handleDoneTodo(payload) {
      payload.done = !payload.done;
    },
    handleDeleteTodo(payload) {
      const indexTask = this.tasks.indexOf(payload);
      this.tasks.splice(indexTask, 1)
    },
    handleChangePage(componentName) {
      this.currentComponent = componentName;
    },
  }
}
</script>

<style>
.done {
  text-decoration: line-through;
}

button:hover {
  color: blue !important;
  background-color: rgb(165 243 252);;
}
</style>
