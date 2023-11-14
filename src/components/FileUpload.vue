<template>
  <div class="file-upload">
    <div class="file-upload__add">
      <Button title="Upload image" />
      <input
        type="file"
        id="profile-image"
        name="profile-image"
        accept="image/png, image/jpeg"
        @change="handleFileUpload($event)"
        class="file-upload__add__input"
      />
    </div>
    <div v-if="fileAdded" class="file-upload__remove">
      <Button title="Delete picture" button-class="button--hollow" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

import Button from './Button.vue'

export default defineComponent({
  name: 'FileUpload',
  components: {
    Button
  },
  emits: ['upload'],
  setup(props, ctx) {
    const fileAdded = ref(false)

    function handleFileUpload(event: { target: { files: any[] } }) {
      const file = event.target.files[0]

      const reader = new FileReader()
      reader.onload = (event) => {
        if (event.target?.result) ctx.emit('upload', event.target?.result.toString())

        fileAdded.value = true
      }

      reader.readAsDataURL(file)
    }

    return {
      handleFileUpload,
      fileAdded
    }
  }
})
</script>

<style scoped>
.file-upload {
  display: flex;
}

.file-upload__add {
  position: relative;
}

.file-upload__remove {
  margin-left: 0.5rem;
}

.file-upload__add__input {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  opacity: 0;
  cursor: pointer;
}
</style>
