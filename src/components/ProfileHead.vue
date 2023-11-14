<template>
  <div class="profile-head">
    <div class="profie-head__info">
      <div class="profile-head__info__picture">
        <svg
          v-if="profileImageUrl === ''"
          width="32"
          height="32"
          viewBox="0 0 32 32"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M16 18C20.9706 18 25 13.9706 25 9C25 4.02938 20.9706 0 16 0C11.03 0 7 4.02938 7 9C7 13.9706 11.0312 18 16 18ZM21.9438 20H10C4.4775 20 0 24.4769 0 30C0 31.1044 0.895625 32 1.94375 32H30C31.1044 32 31.9438 31.1044 31.9438 30C32 24.475 27.525 20 21.9438 20Z"
            fill="#83888F"
          />
        </svg>
        <img v-else :src="profileImageUrl" />
      </div>
      <div class="profile-head__info__titles">
        <h1>{{ title }}</h1>
        <p class="font-small font-color-alternative">{{ subTitle }}</p>
      </div>
    </div>
    <div class="profile-head__upload">
      <FileUpload @upload="uploadImage($event)" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

import FileUpload from './FileUpload.vue'

export default defineComponent({
  name: 'ProfileHead',
  components: {
    FileUpload
  },
  props: {
    title: {
      type: String,
      required: true
    },
    subTitle: {
      type: String,
      required: true
    }
  },
  setup() {
    const profileImageUrl = ref('')

    function uploadImage(url: string) {
      profileImageUrl.value = url
    }

    return {
      uploadImage,
      profileImageUrl
    }
  }
})
</script>

<style scoped>
.profile-head {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.profie-head__info {
  display: flex;
  align-items: center;
}

.profile-head__info__picture {
  border: var(--border-light-grey);
  width: 7.5rem;
  height: 7.5rem;
  border-radius: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: var(--color-light-grey2);
  overflow: hidden;
}

.profile-head__info__titles {
  margin-left: var(--gap-small);
}
</style>
