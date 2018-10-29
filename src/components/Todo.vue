<template>
    <div class="todo">        
        <div class="container">
            <h1>Tasks</h1>                  
            <form v-on:submit="addTask">
                <input type="text" class="add-new-task" v-model="newTask.title" placeholder="Add new task">
                <input type="submit" value="Add">
            </form>
            <ul>
                <li class="new-task-li" v-for="task in tasks"> 
                    <b-form-checkbox v-model="task.completed">
                        <span class="new-task" :class="{completed: task.completed}">
                        {{task.title}}
                        
                    </span>
                        </b-form-checkbox> 
                        <button v-on:click="deleteTask(task)">x</button>                    
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
      this.tasks.push({
        title: this.newTask.title,
        completed: false
      });
      e.preventDefault();
    },
    deleteTask: function(task) {
      this.tasks.splice(this.tasks.indexOf(task), 1);
    }
  }
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}

h1 {
  /* position: absolute; */
  width: 100%;
  font-size: 80px;
  font-weight: 100;
  text-align: center;
  color: rgba(175, 47, 47, 0.15);
}

.add-new-task {
  width: 80%;
  max-width: 800px;
}

.new-task{
    pointer-events: none;
}

.new-task-li{
    margin-top: 30px;
}
</style>