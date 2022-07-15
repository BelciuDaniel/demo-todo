<script setup>
import ToDoListItem from './ToDoListItem.vue';
import { reactive, Ref,watch } from 'vue';
const response = await fetch('https://jsonplaceholder.typicode.com/todos');
const todos = await response.json();
const nameVar = "def";
todos.slice(0,10);
const reactiveTodos = ref(todos);

function handleToDoItemDeleted(toDoItemDeleted){
    reactiveTodos.value=reactiveTodos.value.filter(item=>item.id!==toDoItemId);
}
function handleToDoItemCompleted(){
     reactiveTodos.value = reactiveTodos.value.map(todo => {
        if (todo.id === todoItemId) {
            return {
                ...todo,
                completed: completed
            }
        } else {
            return todo;
        }
    });
    counter.updated++;
}
const checkbox = ref(true);
watch(checkbox, newValue => {
    console.log(`checkbox: ${newValue}`);
});
</script>

<template>
    <div class="grid-container">
    <div class="tableTitle1">Completed</div>
    <div class="tableTitle2">Text</div>
    <div class="tableTitle3">Delete</div>
    </div>
    <ul>
        <ToDoListItem
            v-for="todo of todos"
            :key="todo.id"
            :id="todo.id"
            :title="todo.title"
            :completed="todo.completed"
            @toDo-item-deleted="handleToDoItemDeleted(todo.id)"
            @to-do-item-completed="completed =>handleToDoItemCompleted(todo.id,completed)"
        />
    </ul>
</template>

<style scoped>
.grid-container {
  display: grid;
  grid-template-columns: auto auto auto auto;
  grid-gap: 10px;
  grid-column-gap: 10px;
  padding: 10px;
  grid: 50px / 100px auto 70px;
  background-color: rgb(3, 190, 144);
}

.grid-container > div {
  background-color: rgb(1, 145, 109);
  text-align: center;
  padding: 15px 0;
  font-size: 20px;
}
.tableTitle1{
    color:white;
    outline-color:black;
    outline-width: 50px;
}
.tableTitle2{
    color:white;
    outline-color:black;
    outline-width: 50px;
}
.tableTitle3{
    color:white;
    outline-color:black;
    outline-width: 50px;
}
</style>