<template>
  <div id="sidebar">
       <Slide class="sidebar" isOpen disableEsc noOverlay>            
          <div v-for="todo in todoList">
            <a href="#" @click="openTodo(todo)"><span>{{todo.title}}</span></a>
          </div>        
    </Slide>    
  </div>
</template>

<script>
import { Slide } from 'vue-burger-menu'
export default {
  name: 'sidebar',
  components: {    
    Slide
  },
  data() {
    return{
      todoList: [],
    }
  },
  methods: {
    openTodo: function(todo) {
      console.log(todo);
      localStorage.setItem('todos', JSON.stringify(todo));
    }
  },
  mounted(){
    if(localStorage.getItem('todoList')){
      this.todoList = JSON.parse(localStorage.getItem('todoList'));
    }
  }
}
</script>

<style>
.bm-overlay {
      background: white;
    }

.bm-item-list>div>*>span {
    color: #fff;
    font-weight: 700;
    margin-left: 10px;
}
</style>