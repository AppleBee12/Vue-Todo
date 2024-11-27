<script setup>
import { reactive, ref} from 'vue';
import Todo from './components/TodoItem.vue';
const todoText = ref('');

const addtodo = (e)=>{
  todoText.value = e.target.value;
  const todoTextLength = todoText.value.trim().length;
  // todoText.value = e.target.value;
  //빈칸 없애기. 대상.trim()
  if(todoText.value.trim().length > 0){
    todos.push({ id: todoTextLength+1, title:'todoText', checked: false })
  }
  todoText.value='';
}

 const todos = reactive([
  {id:1,title:'수업 강의 다시 듣기', checked:false},
  {id:2,title:'이력서 다시 쓰기', checked:false},
  {id:3,title:'React 이력서 Page만들기', checked:false},
  {id:4,title:'프로젝트 깃허브 Readme달기', checked:false},
  {id:5,title:'3차 깃허브 수정부분 수정하기', checked:false},
  {id:6,title:'Vue 강의듣기', checked:false},
  {id:7,title:'CS 수업 듣기', checked:false},
  {id:8,title:'javascript 수업듣기', checked:false}
])

rconst toggleCheckbox = ({id, checked})=>{
  const idx = todos.findIndex((todo) => todo.id === id);
  todos[idx].checked = checked
  // console.log(id, checked, todos);
}

</script>

<template>
 <div id="app" class="container">
  <h1>Vue Todo App</h1>
  <!-- 입력 내용이 실시간 반영
  <BFormInput placeholder="할일을 입력하세요" v-model="todoText"/>
  <Todo :todo="todoText"/> -->

  <!-- 입력 후 엔터시 내용이 추가 -->
  <BFormInput placeholder="할일을 입력하세요" @keyup.enter="addtodo" v-model="todoText"/>
  <Todo
  v-for="todo in todos"
  :key="todo.id"
  :todo="todo"
  @toggle-checkbox="toggleCheckbox"
 />

 </div>
</template>

<style scoped>
</style>
