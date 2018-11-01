<template>
    <div class="todo">        
        <div class="container">
            <h1>Tasks</h1>                  
            <form v-on:submit="addTask">
                <input type="text" class="add-new-task" v-model="newTask.title" placeholder="Add new task">           
                <button class="btn" type="submit">Add</button>
            </form>
            <ul>
                <li class="new-task-li" v-for="task in tasks"> 
                    <b-form-checkbox v-model="task.completed">
                        <span class="new-task" :class="{completed: task.completed}">
                        {{task.title}}
                        </span>
                    </b-form-checkbox> 
                     <button
                        class="item-remove"
                        v-on:click="deleteTask(task)">
                        <font-awesome-icon class="trash" icon="trash" />   
                     </button>                                
                    <!-- <input type="checkbox" class="toggle" v-model="task.completed"> -->
                    
                </li>
            </ul>
        </div>        
    </div>
</template>

<script>
export default {
  name: "todo",
  data() {
    return {
      newTask: {},
      tasks: []
    };
  },
  methods: {
    addTask: function(e) {
      if(this.newTask.title){
        this.tasks.push({
          title: this.newTask.title,
          completed: false
        });
        this.newTask.title = "";
      }      
      e.preventDefault();
    },

    deleteTask: function(task) {
      this.tasks.splice(this.tasks.indexOf(task), 1);
    }
  }
};
</script>

<style scoped>
.container{
  margin: auto;
  position: relative;
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}

.completed {
  text-decoration: line-through;
}

h1 {
  /* position: absolute; */
  width: 100%;
  font-size: 80px;
  font-weight: 100;
  text-align: center;
  color: #4fc08d;
}

.new-task{
    pointer-events: none;
    width: 100%;    
}

.item-remove {
    margin-left: .5em;
    background: none;
    border: 1px solid;
    color: #4fc08d;
    padding: 0;
    line-height: 1;
    width: 2em; 
    height: 2em;
    display: initial;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    font-size: 100%;
  }

li{
    margin-top: 30px;
    list-style: none;    
}

ul
{
    list-style-type:none;
    padding:0 0 0 3em;
    margin:0px;
}

.trash, .plus{
  cursor: pointer;
  color: #4fc08d;
}

.btn {
  font-size: 14px;
  margin: 0 .5em;
  border-radius: 2em;
  padding: 0.75em 1.5em;
  cursor: pointer;
  background: none;
  color: darken(#4fc08d, 20%);
  border: 1px solid;
  letter-spacing: 1px;
  /* font-family: $font-family; */
  color: #4fc08d;
  border: #4fc08d 1px solid;
  transition: 250ms ease-out;
}
  .btn:hover, .btn:focus {
    color: #fff;
    background: #4fc08d;
  }


form {
  width: 100%;
  padding: 1.5rem 1rem 0 1rem;
  display: flex;
  }
  form input {
    width: 100%;
    font-size: 14px;
    margin: 0 .5em;
    border-radius: 2em;
    padding: 0.75em 1.5em;
    background: none;
    /* font-family: $font-family; */
    border: #e3e3e3 1px solid;
    transition: border 250ms ease-out;
    }

    form input:focus {
      border: #4fc08d 1px solid;
      outline: none;
    }
    
  



</style>