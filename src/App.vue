<script setup>

  import { RouterLink, RouterView } from 'vue-router'
  import { ref } from 'vue';
  import Todo from './components/TodoItem.vue';

  const todoText = ref(''); // 빈 문자열

  const addtodo = (e) => {
    todoText.value = e.target.value;
  }

</script>

<template>
  <div id="app" class="container">
    <h1 class="mb-5">Vue Todo App</h1>
    <!-- 입력 내용 실시간 반영
    <BFormInput
      placeholder="할 일을 입력하세요."
      v-model="todoText"
    />
    <Todo :todo="todoText"/> -->
    <!-- ↓ 입력 후 엔터 시 내용 추가 -->
    <BFormInput
      placeholder="할 일을 입력하세요."
      @keyup.enter="addtodo"
    />
    <Todo :todo="todoText"/>
  </div>
</template>

<style scoped>

</style>
