<template>
  <section>
    <header>
      <h3>{{ name }}</h3>
    </header>
    <task-list :listId="listId" :tasks="tasksList"></task-list>
  </section>
</template>

<script>
import {mapGetters, mapActions} from 'vuex'
import TaskList from './TaskList'

export default {
  name: 'column',
  components: {TaskList},
  props: {
    listId: String,
    name: String
  },
  computed: {
    ...mapGetters([
      'getTasksFromList'
    ]),
    tasksList () {
      return this.getTasksFromList(this.listId)
    }
  },
  methods: {
    ...mapActions([
      'fetchTasks'
    ])
  },
  created () {
    this.fetchTasks({list: this.listId})
  }
}
</script>

<style scoped>
section {
  box-sizing: border-box;
  background-color: #eceff1;
  border-radius: 3px;
  box-shadow: 0 0 0 0.5px rgba(49, 49, 93, 0.03), 0 2px 5px 0 rgba(49, 49, 93, 1), 0 1px 2px 0 rgba(0, 0, 0, 0.08);
  padding: 1 rem;
  width: 100%;
  max-width: 900px;
  margin: 1rem auto;
  padding: 20px;
}
header{
    color: #37474f;
    margin: 0;
    padding-bottom: 1rem;
}
h3{
    margin: 0;
}
</style>
