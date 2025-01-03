<script setup>
import { ref } from 'vue';
import PostForm from '@/components/PostForm.vue';
import PostList from '@/components/PostList.vue';

let username = 'dasd';
let count = ref(0);
let isDarkTheme = ref(true);

let posts = ref([]);

function incrementCount(event) {
  count.value = ++count.value;
  console.log(count);
}

function addPost(postData) {
  posts.value.push(postData);
}

function deletePost(id) {
  posts.value = posts.value.filter(post => post.id !== id);
}
</script>

<template>
  <div>
    <div class="d-flex p-2 flex-column" :class="{'is-dark': isDarkTheme}">
      <h1>Hello, {{ username.toUpperCase() }}</h1>
      <button @click="incrementCount" class="btn btn-primary">Counter: {{ count }}</button>
      <button @click="isDarkTheme = !isDarkTheme">переключить тему</button>
    </div>
    <PostForm class="p-2 mt-2" @post-added="addPost"/>
    <PostList :posts="posts" @post-delete="deletePost"/>
  </div>
</template>

<style scoped>
  .is-dark {
    color: white;
    background-color: rgb(61, 61, 61);
  }
</style>
