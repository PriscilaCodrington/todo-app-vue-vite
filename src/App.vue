<script>
export default {
  name: "Todo App",
  data() {
    return {
      task: "",
      editedTaskIndex: null,
      statuses: ["to-do", "in-progress", "finished"],
      tasks: [
        {
          name: "Create a todo app",
          status: "to-do",
        },
        {
          name: "Learning Vue.js",
          status: "in-progress",
        },
        {
          name: "Have coffee",
          status: "finished",
        },
      ],
    };
  },
  computed: {
    shouldShowCongratulations() {
      // write your code here
    },
  },
  methods: {
    changeStatus(task) {
      // write your code here
    },
    getStatusClass(task) {
      // write your code here
    },
    deleteTask(index) {
      // write your code here
    },
    editTask(index) {
      // write your code here
    },
    submitTask() {
      // write your code here
    },
  },
};
</script>

<template>
  <div class="container" style="max-width: 600px">
    <!-- Heading -->
    <h2 class="text-center mt-5">Todo App</h2>

    <!-- Input -->
    <div class="d-flex mt-5">
      <input
          type="text"
          placeholder="Enter task"
          class="w-100 form-control"
      />
      <button class="btn btn-warning rounded-0">
        SUBMIT
      </button>
    </div>

    <!-- Task table -->
    <table class="table table-bordered mt-5">
      <thead>
      <tr>
        <th scope="col">Task</th>
        <th scope="col" style="width: 120px">Status</th>
        <th scope="col" class="text-center">#</th>
        <th scope="col" class="text-center">#</th>
      </tr>
      </thead>
      <tbody>
      <tr>
        <td>
            <span class="">
              --- task name ---
            </span>
        </td>
        <td>
            <span
                class="pointer"
            >
              -- task status --
            </span>
        </td>
        <td class="text-center">
          <div>
            <span class="fa fa-trash pointer"/>
          </div>
        </td>
        <td class="text-center">
          <div>
            <span class="fa fa-pen pointer"/>
          </div>
        </td>
      </tr>
      </tbody>
    </table>
    <div>
      Congratulations! You completed all your tasks!
    </div>
  </div>
</template>

<style>
body {
  font-family: 'Montserrat', sans-serif;
}

.pointer {
  cursor: pointer;
}

.line-through {
  text-decoration: line-through;
}
</style>