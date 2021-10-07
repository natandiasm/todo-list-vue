<template>
    <input @keyup.enter="addTodo(inputTodo)" type="text" placeholder="O que você tem para fazer ?" v-model="inputTodo"/>
    <button @click="addTodo(inputTodo)">Adicionar tarefa</button>
    <ul>
        <h4 v-if="todos.length < 1">;) Lista Vazia, adicione uma tarefa.</h4>
        <li v-for="todo in todos" :key="todo.id">
           <span>{{todo.id}}</span> {{todo.text}}
        </li>
    </ul>
    <button @click="clearList">Limpar Lista</button>
</template>

<script>
export default {
    name:"TodoList",
    data() {
        return {
            inputTodo: "",
            todos: [],
        }
    },
    methods: {
        addTodo(text){
            if(text != ""){
                this.todos.push({
                id: this.todos.length + 1, 
                text,
                });
            }
            this.clearInput()
        },
        clearInput(){
            this.inputTodo = "";
        },
        clearList(){
            this.todos = []
        }
    }
}
</script>

<style>
    ul{
        max-width: 50vw;
        margin: 20px auto;
    }

    li{
        list-style: none;
        width: fit-content;
        height: fit-content;
        background: #f9f9f9;
        margin: 10px auto;
        border-radius: 20px;
        padding: 10px 30px 10px 0px;
    }

    span{
        background: #00c6ff;  
        background: -webkit-linear-gradient(to right, #00c6ff, #0072ff);
        background: linear-gradient(to right, #00c6ff, #0072ff); 
        padding: 10px 20px;
        border-radius: 20px 10px 0px 20px;
        margin-right: 20px;
        color: #fff;
        font-weight: 600;
    }

    input{
        height: 40px;
        width: 50%;
        padding: 0px 20px;
        border: none;
        background: #f9f9f9;
        font-size: 18px;
        border-radius: 20px;
    }

    button{
        font-size: 15px;
        padding: 10px 20px;
        background: #8e2de2; 
        background: -webkit-linear-gradient(to right, #8e2de2, #4a00e0);
        background: linear-gradient(to right, #8e2de2, #4a00e0);
        border: none;
        color: #fff;
        border-radius: 30px;
        transition: background 1s ease-out;  
    }
    button:hover{
        background: -webkit-linear-gradient(to right, #4a00e0, #8e2de2);
        background: linear-gradient(to right, #4a00e0, #8e2de2);
    }
</style>