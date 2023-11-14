
<template>
  <main class="main">
    <Card>
      <template v-slot:header>
        <ProfileHead title="Profile" sub-title="Update your profile information" />
      </template>
    </Card>
  </main>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

import Card from './components/Card.vue';
import ProfileHead from './components/ProfileHead.vue';

export default defineComponent({
  components: {
    Card,
    ProfileHead
  },
  setup() {
    
  }
})
</script>

