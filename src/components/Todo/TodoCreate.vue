<template>
  <div>
    <div class="flex mb-4 items-center">
      <div>
        <div class="mb-5">
          <label for="name" class="mb-3 block text-base">
            Todo Name
          </label>
          <input v-model="formData.name" type="text" name="name" id="name" placeholder="Todo Name"
                 class="w-full rounded-md border border-[#e0e0e0] bg-white py-2 px-3 text-base outline-none focus:border-[#6A64F1] focus:shadow-md"/>
        </div>
        <div>
          <button
              @click="handleCreateTodo"
              class="flex-no-shrink p-2 border-2 rounded text-red border-red hover:text-white hover:bg-red">
            Submit
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoCreate",
  props: {
    msg: String,
  },
  data() {
    return {
      formData: {
        name: ''
      }
    }
  },
  methods: {
    handleCreateTodo() {
      this.$emit('createTodo', this.formData)
    }
  }
};
</script>

<style>
</style>