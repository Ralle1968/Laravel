<template>      
<div class="container"> 
<div class="row">
<div class="col-sm-6">    
<h1>Ralfs Todo-Liste</h1>    
    <div id="todo-list-example">
        <ul class="list-group">
            <li class="list-group-item" v-for="(todo, index) in todos" v-bind:title="todo.title" v-bind:class="{'completed' : todo.completed}" >
                {{ todo.title }}
                <button v-on:click="removeTodo(index)" class="btn btn-warning btn-xs pull-right" > Löschen </button>          
            </li>
        </ul>
        <br>
        <input v-model="newTodo.title" v-on:keyup.enter="addNewTodo(newTodo)" class="form-control" placeholder="Hier neuen ToDo eingeben">
    </div>
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
