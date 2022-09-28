<template>
  <div :class="[task.reminder && 'reminder']" class="task">
    <h3>{{task.text}}
      <div @click="onDelete(task.id)" class="fas">+</div>
    </h3>
    <p>{{task.day}}</p>
  </div>
  
</template>
<script>
  export default {
    name:'Task',
    props: {
      task : Object
    },
    methods:{
      onDelete(id){
        console.log(id)
        
      }
    }
  }
</script>
<style scope>
.fas {
  color: red;
  transform: rotate(45deg);
  font-size: 30px;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>