<template>
    <div class="todo">        
        <div class="container">
            <h1>Tasks</h1>    
            <input type="text" v-model="todo.title" placeholder="Title">     
                 
            <form v-on:submit="addTask">               
                <input type="text" class="add-new-task" v-model="newTask.description" placeholder="Add new task">           
                <button class="btn" type="submit">Add</button>
            </form>
            <ul>
                <li class="new-task-li" v-for="task in todo.tasks"> 
                    <b-form-checkbox v-model="task.completed">
                        <span class="new-task" :class="{completed: task.completed}">
                        {{task.description}}
                        </span>
                    </b-form-checkbox> 
                     <button
                        class="btn item-remove"
                        v-on:click="deleteTask(task)">
                        <font-awesome-icon class="trash" icon="trash" />   
                     </button>                   
                </li>
            </ul>

            <button
              class="btn"
              v-on:click="createTodoList(todo)">
              ADD TODO LIST
            </button>
        </div>        
    </div>
</template>

<script>
export default {
  name: "todo",
  data() {
    return {
      newTask: {},
      todo: {
        title: "",
        tasks: [],
      }, 
      todoList: []    
    };
  },
  methods: {
    addTask: function(e) {           
      if (this.newTask.description) {        
        this.todo.tasks.push({          
          description: this.newTask.description,
          completed: false
        });
        this.newTask.description = "";
      }
      e.preventDefault();
    },    
    deleteTask: function(task) {
      this.todo.tasks.splice(this.todo.tasks.indexOf(task), 1);
    },
    createTodoList: function(todo) {
      if(todo.title && todo.tasks.length){
        this.todoList.push(todo);      
        localStorage.setItem('todoList', JSON.stringify(this.todoList));
      }      
    }
  },

  mounted(){
    console.log('App mounted!');
    if(localStorage.getItem('todos')){
      this.todo = JSON.parse(localStorage.getItem('todos'));
    }
  }, 
  watch: {
    todo: {
      handler() {        
        localStorage.setItem('todos', JSON.stringify(this.todo));
      },
      deep: true,
    },
  },
};
</script>


<style scoped>
.container {
  margin: auto;
  position: relative;
  font-family: "Lato", "Lucida Grande", "Lucida Sans Unicode", Tahoma,
    Sans-Serif;
}

.completed {
  text-decoration: line-through;
  color: #ccc;
}

h1 {
  /* position: absolute; */
  width: 100%;
  font-size: 80px;
  font-weight: 100;
  text-align: center;
  color: #4fc08d;
}

.trash,
.plus {
  cursor: pointer;
  color: #4fc08d;
}

.trash:hover {
  color: #fff;
  background: #4fc08d;
}

.btn {
  font-size: 14px;
  margin: 0 0.5em;
  border-radius: 2em;
  padding: 0.75em 1.5em;
  cursor: pointer;
  background: none;
  color: darken(#4fc08d, 20%);
  border: 1px solid;
  letter-spacing: 1px;
  color: #4fc08d;
  border: #4fc08d 1px solid;
  transition: 250ms ease-out;
}
.btn:hover,
.btn:focus{
  color: #fff;
  background: #4fc08d;
}

.btn:hover > .trash{
  color: #fff;
}

form {
  width: 100%;
  padding: 1.5rem 1rem 0 1rem;
  display: flex;
}
form input {
  width: 100%;
  font-size: 14px;
  margin: 0 0.5em;
  border-radius: 2em;
  padding: 0.75em 1.5em;
  background: none;
  border: #e3e3e3 1px solid;
  transition: border 250ms ease-out;
}

form input:focus {
  border: #4fc08d 1px solid;
  outline: none;
}

li {
  list-style: none;
  width: 100%;
  display: flex;
  padding: 2.5rem 2rem 0 1rem;
}

ul {
  list-style-type: none;
  padding: 0 0 0 2em;
  margin: 0px;
  width: 100%;
}

.new-task {
  pointer-events: none;
  width: 100%;
}

.item-remove {
  
  background: none;
  border: 1px solid;
  color: #4fc08d;
  padding: 0;
  line-height: 1;
  width: 2em;
  height: 2em;
  border-radius: 50%;
  font-size: 100%;
  
}


.custom-control-inline{
  width: 100%
}

</style>