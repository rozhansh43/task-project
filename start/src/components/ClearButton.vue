<template>
  <div>
    <div class="clearBtns">
      <button @click="$emit('clearCompleted')">
        Clear completed
      </button>

      <button @click="$emit('clearAll')">
        Clear all
      </button>
    </div>
  </div>
</template>