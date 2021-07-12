<template>
  <div>
    <li>
      <button>
        <i class="far fa-circle" aria-hidden="true">
        </i>
        {{ task.title }}
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
  props: ['task']
}
</script>