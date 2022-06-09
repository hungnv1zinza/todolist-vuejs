<template>
  <div class="h-100 w-full flex items-center justify-center bg-teal-lightest font-sans">
    <div class="bg-white rounded shadow p-6 m-4 w-full lg:w-1/2 lg:max-w-3/4">
      <div class="mb-4">
        <h1 class="text-grey-darkest">Todo List</h1>
        <div class="flex mt-4">
          <input class="shadow appearance-none border rounded w-full py-2 px-3 mr-4 text-grey-darker"
                 placeholder="Add Todo">
          <button class="flex-no-shrink p-2 border-2 rounded text-teal border-teal hover:text-white hover:bg-teal">Search
          </button>
        </div>
      </div>
      <div v-for="(task, index) in tasks" :key="index">
        <div class="flex mb-4 items-center">
          <p class="w-full text-grey-darkest">{{ task.name }}</p>
          <button
              class="flex-no-shrink p-2 ml-4 mr-2 border-2 rounded hover:text-white text-green border-green hover:bg-green">
            Done
          </button>
          <button class="flex-no-shrink p-2 ml-2 border-2 rounded text-red border-red hover:text-white hover:bg-red">
            Remove
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        {name: 'Task 1', done: false},
        {name: 'Task 2', done: false},
        {name: 'Task 3', done: false},
        {name: 'Task 4', done: false},
      ]
    }
  }
}
</script>

<style>
button:hover {
  color: blue !important;
  background-color: rgb(165 243 252);;
}
</style>