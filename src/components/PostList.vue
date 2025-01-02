<template>
  <Post @post-delete="deletePost" :post="post" v-for="post in posts" />
</template>

<script setup>

import Post from '@/components/UI/Post.vue';

let emit = defineEmits(['post-delete']);
defineProps(['posts']);

function deletePost(id) {
  emit('post-delete', id)
}

</script>
