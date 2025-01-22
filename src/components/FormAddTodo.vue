<template>
    <div class="form-inline">
            <div class="form-group">
               <input type="text" class="form-control mx-sm-3" placeholder="i want to do ..." v-model="todoText">
               <button class="btn btn-primary" @click="addTodo">add</button>
            </div>
          </div>
</template>
<script >
 export default{
   emits:['add-todo'],
data() {
   return {
      todoText:''
   }
},
methods:{
   addTodo(){
      console.log(this.todoText);
      
      this.$emit('add-todo',this.todoText )
     this.todoText='';
   }
}
 }  
</script>