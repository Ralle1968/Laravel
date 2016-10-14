<template>      
<div class="container"> 
    <div class="row">
        <div class="col-sm-6">    
            <h1>Ralfs Todo-Liste</h1>    
                <div id="todo-list-example">
                    <ul class="list-group">
                        <li class="list-group-item" v-for="(todo, index) in todos" v-bind:title="todo.title" v-bind:class="{'completed' : todo.completed}" data-toggle="tooltip" title="" >
                        {{ todo.title }}
                        <button v-on:click="removeTodo(index)" class="btn btn-warning btn-xs pull-right" >
                        <span data-toggle="tooltip" title="Löschen!" class="glyphicon glyphicon-trash"></span>
                        </button>         
                        </li> 
                    </ul>
                </div> 
        </div>       
    </div>
        <br>
    <div class="row">    
        <div class="col-sm-6">
            <form @submit.prevent="addNewTodo(newTodo)">
                <div class="input-group">
                    <input type="text" class="form-control" placeholder="Hier neuen ToDo eingeben" v-model="newTodo.title">
                    <span class="input-group-btn">
                        <button class="btn btn-success">Hinzufügen</button>
                    </span>
                </div>
            </form>
        </div>
    </div>
</div>

</template>

<script>
export default {
    props: ['title'],

    data(){
        return {
            newTodo: {title: '', completed: false},
            todos: [
              {title: 'ToDo-App erstellen', completed: true},
              {title: 'Termin eintragen', completed: false},
              {title: 'Fenster putzen', completed: false}
            ]
        };
    },

    methods: {
        addNewTodo: function (newTodo) {
          this.todos.push(newTodo)
          this.newTodo = {title: '', completed: false}
        },

        removeTodo: function(index) {
            this.todos.splice(index, 1)
        }
    },

        mounted() {
            console.log('Component <simple> ready.');
        }
}
</script>
