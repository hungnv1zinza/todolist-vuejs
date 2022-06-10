<template>
  <div class="h-100 w-full flex items-center justify-center bg-teal-lightest font-sans">
    <div class="bg-white rounded shadow p-6 m-4 w-full lg:w-1/2 lg:max-w-3/4">
      <div class="mb-4">
        <h1 class="text-grey-darkest">{{ title }}</h1>
        <button @click="handleToggle"
                class="flex-no-shrink p-2 border-2 rounded text-teal border-teal hover:text-white hover:bg-teal">
          {{ button }}
        </button>
      </div>
      <component
          :tasks="tasksFiltered"
          :is="currentComponent"
          @createTodo="handleCreateTodo"
          @doneTodo="handleDoneTodo"
          @deleteTodo="handleDeleteTodo"
          @search="handleSearch"
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
      title: "Todo List",
      button: "Add New Todo",
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
        ...payload,
        done: false
      })
      this.currentComponent = 'TodoList'
      this.title = "Todo List"
      this.button = 'Add New Todo';
      this.search = '';
    },
    handleDoneTodo(payload) {
      this.tasks.slice(payload, payload + 1)[0].done = true;
    },
    handleDeleteTodo(payload) {
      this.tasks.splice(payload, 1)
    },
    handleToggle() {
      if (this.currentComponent === 'TodoList') {
        this.currentComponent = 'TodoCreate';
        this.title = "Todo Create"
        this.button = 'Back';
      } else {
        this.currentComponent = 'TodoList';
        this.title = "Todo List"
        this.button = 'Add New Todo';
      }
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
