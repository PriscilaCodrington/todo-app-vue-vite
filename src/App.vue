<script>
export default {
  name: "Todo App",
  data() {
    return {
      editedTaskIndex: "",
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
      finish: false,
    };
  },
  computed: {
    shouldShowCongratulations() {
      return this.tasks.every((task) => task.status === "finished");
    },
  },
  methods: {
    changeStatus(task) {
      for (let i = 0; i < this.statuses.length; i++) {
        if (task.status === this.statuses[i]) {
          i++;
          task.status = this.statuses[i];
        } else if (task.status === this.statuses[2])
          task.status = this.statuses[0];
      }
    },
    getStatusClass(task) {
      switch (task.status) {
        case "to-do":
          return "text-danger";
          break;
        case "in-progress":
          return "text-warning";
          break;
        case "finished":
          return "text-success";
          break;
        case "default":
          break;
      }
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTaskIndex = index;
    },
    submitTask() {
      if (this.editedTaskIndex === null) {
        if (this.task.length === 0) return;
        this.tasks.push({
          name: this.task,
          status: "to-do",
        });
      } else {
        this.tasks[this.editedTaskIndex].name = this.task;
        this.editedTaskIndex = null;
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
        v-model="task"
      />
      <button class="btn btn-warning rounded-0" @click="submitTask">
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
        <tr v-for="(task, index) in tasks" :key="index">
          <td>
            <span :class="task.status === 'finished' ? 'line-through' : ''">
              {{ task.name }}
            </span>
          </td>
          <td>
            <span
              class="pointer"
              :class="getStatusClass(task)"
              @click="changeStatus(task)"
            >
              {{ task.status }}
            </span>
          </td>
          <td class="text-center">
            <div @click="deleteTask(index)">
              <span class="fa fa-trash pointer" />
            </div>
          </td>
          <td class="text-center">
            <div @click="editTask(index)">
              <span class="fa fa-pen pointer" />
            </div>
          </td>
        </tr>
      </tbody>
    </table>
    <div v-if="shouldShowCongratulations">
      Congratulations! You completed all your tasks!
    </div>
  </div>
</template>

<style>
body {
  font-family: "Montserrat", sans-serif;
}

.pointer {
  cursor: pointer;
}

.line-through {
  text-decoration: line-through;
}
</style>
