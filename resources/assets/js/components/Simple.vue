<template>      
<div class="container"> 
<div class="row">
<div class="col-sm-6">    
<h1>Ralfs Todo-Liste</h1>    
    <div id="todo-list-example">
        <ul class="list-group">
            <li class="list-group-item" v-for="(todo, index) in todos" v-bind:title="todo" >
                {{ todo }}
                <button v-on:click="removeTodo(index)" class="btn btn-warning btn-xs pull-right" > Löschen </button>          
            </li>
        </ul>
        <br>
        <input v-model="newTodoText" v-on:keyup.enter="addNewTodo" class="form-control" placeholder="Hier neuen ToDo eingeben">
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
            newTodoText: '',
            todos: [
              'ToDo-App erstellen',
              'Termin eintragen',
              'Fenster putzen'
            ]
        };
    },

    methods: {
        addNewTodo: function () {
          this.todos.push(this.newTodoText)
          this.newTodoText = ''
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
