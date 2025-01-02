<template>
  <div class="border p-3 m-3 d-flex justify-content-between" v-for="post in posts" :key="post.id">
    <div>
      <h1>{{ post.title }}</h1>
      <span>{{ post.content }}</span>
    </div>
    <Button @click="$emit('post-delete', post.id)">Удалить пост</Button>
  </div>
</template>

<script setup>
import Button from '@/components/UI/Button.vue';

defineEmits(['post-delete']);
defineProps(['posts']);
</script>
