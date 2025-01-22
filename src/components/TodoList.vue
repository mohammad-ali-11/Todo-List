<template>
<div class="d-flex flex-column align-items-center ">
    <nav class="col-6 mb-3">
        <div class="nav nav-tabs" id="nav-tab" role="tablist">
            <a class="nav-item nav-link active font-weight-bold" id="nav-home-tab">undone <span class="badge badge-second">11</span></a>
            <a class="nav-item nav-link font-weight-bold" id="nav-profile-tab">done <span class="badge badge-success"></span>9</a>
        </div>
    </nav>
    <Todo v-for="(item,idex) in todos" :todo="item" :key="idex" @delete-todo="$emit('delete-todo',$event)" @edit-todo="$emit('edit-todo',$event)"></Todo>
    
</div>  
         
</template>
<script >
import Todo from './Todo.vue';

 export default{
    emits:['delete-todo','edit-todo'],
    props:{
       todos:{
        type:Array,
        required:true
       }
    },
    components:{
        Todo
    }
 }   
</script>
