<template>
  <router-link class="board-card" :to="{name: 'board', params: {name, id}}">
      <span class="board-card-title">{{name}}</span>
  </router-link>
</template>

<script>
export default {
  name: 'board-card',
  props: {
    id: String,
    name: String
  }
}
</script>

<style scoped>
 .board-card{
     background-color: #fff;
     box-shadow: 0 8px 16px -4px rgb(9 30 66 / 25%), 0 0 0 1px rgb(9 30 66 / 8%);
     border: 1px solid rgba(9, 30, 66, 0.08);
     box-sizing: border-box;
     border-radius: 5px;
     color: #172b4d;
     margin: 0.rem 1.5rem;
     padding: 1rem;
     text-align: left;
     text-decoration: none;
     transition: all 600ms ease;
     width: 100%;
     height: 100px;
     margin: 10px 0;
 }
 .board-title{
     font-size: 1.2rem;;
 }
 .board-card:hover{
     background-color: #0079BF;
     font-weight: bold;
     color: #fff;
 }

</style>
