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

      <clear-button @clearCompleted="clearCompleted" @clearAll="clearAll" />
        <p>
          {{ this.tasks}}
        </p>
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
import ClearButton from './ClearButton'

export default {
  name: "Task",
  props: {
    tasks:{ type:Array , default: () => [] }
    },
  components: {
    TaskItem,
    NewTask,
    ClearButton
  },
  data() {
    return {
    
    }
  },
  computed: {
    incomplete () {
      return this.tasks.filter(this.inProgress).length
    }
  },
  methods: {
    add (newTask) {
      this.tasks.push({
        id: String(Math.floor(Math.random() * 999999999)),
        title: newTask,
        completed: false,
        newTask,
      })
    },
    inProgress (task) {
      return !this.isCompleted(task)
    },
    isCompleted (task) {
      return task.completed
    },
    clearCompleted () {
      this.tasks = this.tasks.filter(this.inProgress)
    },
    clearAll () {
      this.tasks = [];
    },
    removeTask (index) {
      this.tasks.splice(index, 1)
    },
    completeTask (task) {
      task.completed = !task.completed;
    }
  }
};
</script>
