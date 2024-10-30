<template>
  <div class="bg-[#333] w-screen h-screen flex justify-center items-center">
    <!-- کل پروژه -->
    <div class="max-w-md mx-auto p-4 bg-[#dedde9] shadow-md rounded-md">
      <!-- Header -->
      <h2 class="text-2xl font-bold mb-4 text-center">To-Do List</h2>
      <div class="flex mb-4">
        <!-- فیلد وروردی -->
        <input
          v-model="newTask"
          placeholder="Add a new task"
          @keyup.enter="addTask"
          class="flex-1 p-2 border border-gray-300 rounded-l-md"
        />
        <button
          @click="addTask"
          class="px-4 bg-blue-500 text-white rounded-r-md hover:bg-blue-600"
        >
          Add Task
        </button>
      </div>
      <ul class="space-y-2">
        <li
          v-for="(task, index) in tasks"
          :key="index"
          class="flex items-center justify-between bg-white p-2 rounded-md shadow-sm"
        >
          <span :class="{ 'line-through text-gray-500': task.completed }">{{
            task.text
          }}</span>
          <div class="space-x-2">
            <button
              @click="toggleTask(index)"
              class="text-green-500 hover:text-green-700"
            >
              Complete
            </button>
            <button
              @click="removeTask(index)"
              class="text-red-500 hover:text-red-700"
            >
              Delete
            </button>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask, completed: false });
        this.newTask = "";
      }
    },
    toggleTask(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>
