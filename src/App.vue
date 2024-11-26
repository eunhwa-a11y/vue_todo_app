<script setup>

  import { reactive, ref } from 'vue';
  import Todo from './components/TodoItem.vue';

  const todoText = ref(''); // 빈 문자열

  const addtodo = (e) => {
    todoText.value = e.target.value;
    const todoTextLength = todoText.value.trim().length; // 빈칸 없애기 대상.trim()

    if(todoTextLength > 0){
      // 값이 있다면 todos에 값 추가
      todos.push({id : todoTextLength+1, title : todoText.value, checked : false})
    }
    todoText.value = '';
  }

  const todos = reactive([
    {id : 1, title : '웹 배우기', checked : false},
    {id : 2, title : '취직하기', checked : false},
  ])

  const toggleChecbox = (id, checked) => {
    // 대상.findIndex(각 요소 => { return 조건 })
    const idx = todos.findIndex( todo => todo.id === id ); // return, 중괄호 생략
    todos[idx].checked = checked
    console.log(id, checked, todos.values); // {id: 1, checked: true} checked:true id:1
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
      v-model="todoText"
    />
    <Todo
      v-for= "todo in todos"
      :key="todo.id"
      :todo="todo"
      v-model="todoText"
      @toggle-checkbox="toggleChecbox"
    />
  </div>
</template>

<style scoped>


</style>
