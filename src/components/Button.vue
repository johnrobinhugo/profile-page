<template>
  <button type="button" class="button" :class="buttonClass">{{ title }}</button>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Button',
  props: {
    title: {
      type: String,
      required: true
    },
    buttonClass: {
      type: String
    }
  }
})
</script>
