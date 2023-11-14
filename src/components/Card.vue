<template>
  <div class="card">
    <div v-if="$slots.header" class="card__header">
      <slot name="header"></slot>
    </div>
    <div v-if="$slots.body" class="card__body">
      <slot name="body"></slot>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Card'
})
</script>

<style scoped>
.card {
  border: var(--border-light-grey);
  border-radius: 0.3125rem;
  background-color: var(--color-white);
}

.card__header {
  padding: 3.125rem 2rem;
  border-bottom: 1px solid var(--border-light-grey);
}
</style>
