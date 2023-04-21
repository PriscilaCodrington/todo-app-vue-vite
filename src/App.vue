<script>
export default {
  name: "Todo App",
  data() {
    return {
      task: "",
      editedTaskIndex: null,
      statuses: ["to-do", "in-progress", "finished"],
      /* Status could be: 'to-do' / 'in-progress' / 'finished' */
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
  computed: {},
  methods: {
    /**
     * Capitalize first character
     */
    capitalizeFirstChar(str) {
      return str.charAt(0).toUpperCase() + str.slice(1);
    },
    /**
     * Change status of task by index
     */
    changeStatus(task) {
      // task.status = this.statuses[(this.statuses.indexOf(task.status)+1) % this.statuses.length]
      if (task.status === this.statuses[0]) task.status = this.statuses[1]
      else if (task.status === this.statuses[1]) task.status = this.statuses[2]
      else task.status = this.statuses[0]
    },
    getStatusClass(task) {
      if (task.status === 'to-do') return 'text-danger'
      else if (task.status === 'finished') return 'text-success'
      else return 'text-warning'
    },
    /**
     * Deletes task by index
     */
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    /**
     * Edit task
     */
    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTaskIndex = index;
    },
    /**
     * Add / Update task
     */
    submitTask() {
      if (this.task.length === 0) return;
      /* We need to update the task */
      if (this.editedTaskIndex != null) {
        this.tasks[this.editedTaskIndex].name = this.task;
        this.editedTaskIndex = null;
      } else {
        /* We need to add new task */
        this.tasks.push({
          name: this.task,
          status: "to-do",
        });
      }
      this.task = "";
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
              --task status--
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