<template>
  <ul>
    <li
      v-for="(task, index) in tasks"
      :key="index"
      :class="{ completed: task.completed }"
      @click="markAsCompleted({ task })">{{ task.title }}
        <i @click="deleteTask({ taskId: task.id })">X</i>
    </li>
    <input
      type="text"
      placeholder="Añade una nueva tarea"
      v-model="title"
      @keyup.enter="add()"
    />
  </ul>
</template>

<script>
import {mapActions} from 'vuex'
export default {
  name: 'task-list',
  props: {
    listId: String,
    tasks: Array
  },
  data () {
    return {
      title: ''
    }
  },
  methods: {
    ...mapActions([
      'addTask',
      'markAsCompleted',
      'deleteTask'
    ]),
    add () {
      this.addTask({ list: this.listId, title: this.title })
      this.title = ''
    }
  }
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
li {
  background-color: #fafafa;
  border-radius: 3px;
  border-bottom: 1px solid #ccc;
  margin: 0.25rem 0;
  padding: 1rem;
}
ul li i{
  text-transform: initial;
  font-family: initial;
  color: #b50000;
  font-size: 1.2rem;
  padding: 5px;
  font-style: normal;
  cursor: pointer;
}
li.completed {
  background-color: #cfd8dc;
  color: #90a4ae;
}
input {
  box-sizing: border-box;
  background-color: #fff;
  border: 1px solid rgba(9, 30, 66, 0.08);
  border-radius: 3px;
  font-size: .9rem;
  outline: 0;
  padding: 0.5rem;
  color: #172b4d;
  transition: all 600ms ease;
}

input::placeholder {
  color: #172b4d;
}

input:active,
input:focus {
  background-color: #fafafa;
  color: #172b4d;
}
</style>
