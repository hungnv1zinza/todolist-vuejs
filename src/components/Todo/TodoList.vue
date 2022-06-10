<template>
  <div class="flex my-4">
    <input @keyup="$emit('search', $event)"
           class="shadow appearance-none border rounded w-full py-2 px-3 text-grey-darker"
           placeholder="Search Todo">
  </div>
  <div>
    <div class="flex mb-4 items-center" v-for="(task, index) in tasks" :key="index">
      <p :class="{done: task.done}" class="w-full text-grey-darkest">{{ task.name }}</p>
      <button @click="handleDoneTask(index)"
              class="flex-no-shrink p-2 ml-4 mr-2 border-2 rounded hover:text-white text-green border-green hover:bg-green">
        Done
      </button>
      <button @click="handleDeleteTask(index)"
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
    handleDoneTask(index) {
      this.$emit('doneTodo', index)
    },
    handleDeleteTask(index) {
      this.$emit('deleteTodo', index)
    },
  },
}
</script>

<style>
</style>