<template>
  <div class="container">
    <div class="task">

      <div class="title">
        <h1>To Do List</h1>
      </div>

      <new-task @add="add"/>

      <div class="taskItems">
        <ul>
          <task-item 
          :task="task" 
          v-for="(task, index) in tasks"
          @complete="completeTask(task)"
          @remove="removeTask(index)"
          :key="task.id"
          >
          </task-item>
        </ul>
      </div>

      <div class="clearBtns">
        <button @click="clearCompleted">
          Clear completed
        </button>

        <button @click="clearAll">
          Clear all
        </button>
      </div>

      <div class="pendingTasks">
        <span>
          Pending Tasks: {{ incomplete }}
        </span>
      </div>
    </div>
  </div>
</template>

<script>
import TaskItem from './TaskItem'
import NewTask from './NewTask'

export default {
  name: "Task",
  props: ['tasks'],
  components: {
    TaskItem,
    NewTask
  },
  data() {
    return {
    
    }
  },
  computed: {
    incomplete() {
      return this.tasks.filter(this.inProgress).length
    }
  },
  methods: {
    add(name) {
        this.tasks.push({
          title: this.name,
          completed: false,
          id : String(Math.floor(Math.random()*99999999)),
          name,
        });
    },
    inProgress(task) {
      return !this.isCompleted(task)
    },
    isCompleted(task) {
      return task.completed
    },
    clearCompleted() {
      this.tasks = this.tasks.filter(this.inProgress)
    },
    clearAll() {
      this.tasks = [];
    },
    removeTask(index) {
      this.tasks.splice(index, 1)
    },
    completeTask(task) {
      task.completed = !task.completed;
    }
  }
};
</script>
