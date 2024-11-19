<template>
  <h1>{{ title }}</h1>
  <form >
    <input type="text" id="new-task" v-model="newTask" placeholder="input Task">
    <button type="submit" @click="addNewTask">Add</button>
  </form>
  <ul id="todo-lest">
    <li v-for="task in list" class="todo-lest-item">{{ task.content }}

      <button @click="print(task.content)">add</button>
    </li>

    
  </ul>
</template>

<script>
import {ref} from 'vue';
  export default{
    setup(){
      const title = 'ToDo App'
      const newTask = ref('ndjnad')
      const list = ref([
        {id: 1, content: "task 1"},
        {id: 2, content: "task 2"}
      ])

      const addNewTask = (e) => {
        e.preventDefault();
        const id = list.value.length ? list.value[list.value.length - 1].id + 1 : 1;
        const task = { id: id, content: newTask.value };
        list.value.push(task);
      };


      const print = title => {
          console.log(title);
        
      }

      return {title, list, print, newTask}
    }
  }
</script>