<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png"> -->
    
    <h2>TODO APP</h2>
    
    <input type="text" v-model="newTodo" @keyup.enter="addTodo(newTodo)">

    <button @click="addTodo(newTodo)">Add Todo!</button>
    
    <hr>
    
    <button @click="allDone()">All Done!</button>
    
    <ul>
      <li v-for="(t, i) in todos" :key="i" :class="{done : t.done}">
        <input type="checkbox" v-model="t.done"> <span class="title">{{ t.title }}</span> <span class="red" @click="eraseTodo(i)">Erase</span>
      </li>
    </ul>

  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'Home',
  data(){
    return {
      newTodo: '',
      todos: []
    }
  },
  methods: {
    addTodo(nt){
      this.todos.push({
        title: nt,
        done: false,
      });
      this.newTodo = '';
    },
    eraseTodo(t){
      let confirmAction = confirm("Are you sure to execute this action?");
      if (confirmAction) {
        const todoIndex = this.todos.indexOf(t);
        this.todos.splice(t, 1);
      } else {
      }
        
    },
    allDone(){
      this.todos.forEach(todo => {
        todo.done = true
      })
    }
  },
  components: {
    // HelloWorld
  }
}
</script>

<style>
ul {
  max-width:320px;
  padding:20px;
  margin:0 auto;
  list-style:none;
}
ul li {
  display:flex;
  justify-content:space-between;
  align-items:center;
  padding:10px;
  margin-bottom:10px;
}
ul li.done .title {
    text-decoration: line-through;
}
.red {text-decoration:;background-color:red;cursor:pointer;color:#fff;padding:10px 20px;border-radius:10px;}
</style>