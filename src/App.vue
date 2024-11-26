<script setup>

import { RouterLink, RouterView } from 'vue-router'
import TodoItem from './components/TodoItem.vue';

</script>

<template>
  <div id="app" class="container">
    <h1 class="mb-5">Vue Todo App</h1>
    <BFormInput
      placeholder="할 일을 입력하세요."
    />
    <TodoItem
    todo="맛난 거 먹기"/>
  </div>

</template>

<style scoped>

</style>
