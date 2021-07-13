<template>
  <div>
    <form class="form" @submit.prevent="emitAdd">
      <input placeholder="New Task" v-model="name"/>

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
      name: null
    }
  },
  methods: {
    emitAdd() {
    this.$emit('add',this.name)
    this.name= null
    }
  }
}
</script>