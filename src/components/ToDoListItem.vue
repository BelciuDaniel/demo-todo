<script setup>
defineProps({
    id: Number,
    title: String,
    completed: Boolean
})
</script>

<template>
<p></p>
  <div class="grid-container">
  <div class="checkBox"><input type="checkbox" :checked="completed" /></div>  
  <div class="title">{{ title }}</div>
  <div class="deleteButton"><button>Delete</button></div>
</div>
    
</template>

<style scoped>
.grid-container {
  display: grid;
  grid-template-columns: auto auto auto auto;
  grid-gap: 10px;
  grid-column-gap: 10px;
  padding: 10px;
  grid: 50px / 50px auto 70px;
  background-color: rgb(3, 190, 144);
}

.grid-container > div {
  background-color: rgb(1, 145, 109);
  text-align: center;
  padding: 15px 0;
  font-size: 20px;
}
.title{
  background-color: rgb(0, 179, 179);
  text-align: center;
  padding: px 0;
  font-size: 200px;
  color:white;
  text-shadow:
   -1px -1  px 0 #000,  
    1px -1px 0 #000,
    -1px 1px 0 #000,
    1px 1px 0 #000;
}
.checkBox{
    pointer-events:none
}

</style>