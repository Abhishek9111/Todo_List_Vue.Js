<template>
    <div class="container">
        <div class="row">
            <div class="col-12">
                <p class="display-3">Vue Todo list</p>
            </div>
        </div>
        <div class="row">
            <div class="col-12 col-lg-6"><NewTodo
            @on-addTodo = "addTodo($event)"
            /></div>
            
        </div>
        <div class="col-12 col-lg-6">
            <ul class="list-group">
                <Todo v-for="(todo,index) in todos" 
                :key="index" 
                :todoString = 'todo.todoString' 
                :completed='todo.completed'             
                
                @on-delete="deleteTodo(todo)"
                @on-toggle = "toggleTodo(todo)"
                @on-edit = "editTodo(todo, $event)"
                />
                <!--@ is used to pass custom method/functions from parent to child can hold custom names-->
            </ul>
        </div>
    </div>
</template>

<script>
import Todo from './Todo.vue'
import NewTodo from './NewTodo.vue'

export default {
    name:'TodoList',
    components:{
        Todo,NewTodo
    },
    data(){
        return{
            todos:[
                { todoString:'Finish Course', completed: false },
                { todoString:'Keep learning', completed: true },
                { todoString:'finish todo list', completed: false },
                { todoString:'Start Nuxt course', completed: false },
        ]
    }
    },
    methods:{
        addTodo(newTodo){
            this.todos.push({
                todoString: newTodo,
                completed: false  
            })
        },
        toggleTodo(todo){
            todo.completed = !todo.completed
        },
        editTodo(todo, newTodoString){
            todo.todoString = newTodoString
        },
        deleteTodo(delTodo){
            this.todos = this.todos.filter(todo=>todo != delTodo)
        }
    }
}
</script>

<style>

</style>