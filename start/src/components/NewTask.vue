<template>
  <div>
    <form class="form" @submit.prevent="emitAdd">
      <input placeholder="New Task" v-model="newTask"/>

      <button type="submit">
        <i class="fas fa-plus">
        </i>
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: null
    }
  },
  methods: {
    emitAdd() {
    this.$emit('add',this.newTask)
    this.newTask= null
    }
  }
}
</script>