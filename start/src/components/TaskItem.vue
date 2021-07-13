<template>
  <div>
    <li>
      <button @click="$emit('complete')" :class="className">
        <i class="far fa-circle">
        </i>

        <span>
          {{ task.title }}
        </span>
      </button>

      <button @click="$emit('remove')">
        <i class="far fa-trash-alt">
        </i>
      </button>
      </li>
  </div>
</template>

<script>
export default {
  props: {
    task: { type: Array, default: () => [] }
    },
  computed: {
    className() {
      let classes = ['toggle'];
      if(this.task.completed) {
        classes.push('toggle-completed')
      }
      return classes;
    }
  }
}
</script>