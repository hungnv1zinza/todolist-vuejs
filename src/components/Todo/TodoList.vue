<template>
  <div class="mb-4">
    <h1 class="text-grey-darkest">Todo List</h1>
    <button @click="$emit('changePage', 'TodoCreate')"
            class="flex-no-shrink p-2 border-2 rounded text-teal border-teal hover:text-white hover:bg-teal">
      Add New Todo
    </button>
    <div class="mt-4">
      <input @keyup="$emit('search', $event)"
             class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker"
             placeholder="Search Todo">
    </div>
  </div>

  <div>
    <div class="flex mb-4 items-center" v-for="task in tasks" :key="task">
      <p :class="{done: task.done}" class="w-full text-grey-darkest">{{ task.name }}</p>
      <button @click="handleDoneTask(task)"
              class="flex-no-shrink p-2 ml-4 mr-2 border-2 rounded hover:text-white text-green border-green hover:bg-green">
        Done
      </button>
      <button @click="handleDeleteTask(task)"
              class="flex-no-shrink p-2 ml-2 border-2 rounded text-red border-red hover:text-white hover:bg-red">
        Remove
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    msg: String,
    tasks: {
      type: Array,
      default: () => []
    }
  },
  data() {
    return {
      search: ""
    }
  },
  methods: {
    handleDoneTask(task) {
      this.$emit('doneTodo', task)
    },
    handleDeleteTask(task) {
      this.$emit('deleteTodo', task)
    },
  },
}
</script>

<style>
</style>