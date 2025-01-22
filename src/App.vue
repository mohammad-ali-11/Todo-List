<template>
<custom-header></custom-header>
<main>
    <section class="jumbotron">
        <div class="container d-flex flex-column align-items-center">
          <h1 class="jumbotron-heading">Welcome!</h1>
          <p class="lead text-muted">To get started, add some items to your list:</p>
          
          <form-add-todo @add-todo="addTodo"></form-add-todo>
        </div>
    </section>  
    <div class="todosList">
      <div class="container">
        
          <todo-list :todos="todos" @delete-todo="deleteTodo" @edit-todo="editTodo" ></todo-list>
         
      </div>
    </div>
</main>
        
</template>


<script >
import Header from './components/Header.vue';
import TodoList from './components/TodoList.vue';
import FormAddTodo from './components/FormAddTodo.vue';


export default{
  data() {
  return {
    // this.todoText,
    todos: []
  }
},

components:{ 
'custom-header':Header,
 TodoList,
 FormAddTodo
},
methods:{
  addTodo(Text){
this.todos.push({
  key:Date.now(),
  done:false,
  Text
})
    
  },
  deleteTodo(key){
    
    
this.todos=this.todos.filter(item=>item.key!=key)
  },
  editTodo({key,text}){
    console.log(key,text);
    
   this.todos= this.todos.map(item=>{
    if (item.key===key) {
    
     return{
      ...item,
      Text : text
     }
    }
      return item
    
   })
  }
}

}
</script>


<style>
#app {
font-family: Avenir, Helvetica, Arial, sans-serif;
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
text-align: center;
color: #2c3e50;
margin-top: 60px;
}
</style>
