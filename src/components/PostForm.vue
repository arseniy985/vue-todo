<script setup>
import { ref, defineEmits, onMounted, computed, reactive } from 'vue';
    let emit = defineEmits(['post-added']);
    let postData = {title: '', content: '', id: 0}

    let disabled = ref(true)
    function changeText(e) {
        disabled.value = !postData.title || !postData.content
    }

    function createPost(e) {
        e.preventDefault();
        if (!postData.title || !postData.content) return
        emit('post-added', { ...postData})
        postData.id += 1;
        console.log(postData)
        postData.title = ''
        postData.content = ''
        disabled.value = true;
    }
</script>

<template>
    <form class="border d-flex flex-column align-items-center p-3">
        <h1>Создать пост</h1>
        <input @input="changeText" v-model="postData.title" class="mb-2 w-50" id="post-title" type="text" placeholder="Input title">
        <input @input="changeText" v-model="postData.content" class="w-50" id="post-content" type="text" placeholder="Input content">
        <button :disabled="disabled" @click="createPost" id="create-post" class="mt-2 btn btn-secondary" type="submit">Создать пост</button>
    </form>
</template>