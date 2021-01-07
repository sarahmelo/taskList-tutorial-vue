
<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title has-text-left" :class="mode">
       {{hoje}}
      </p>
      <div class="has-text-right">
        <p class="card-header-title">{{tarefas.length}} tarefas</p>
      </div>
    </header>
    <div class="card-content">
      <div class="content">
        <novo-todo @novaTarefa="adicionarTarefa" :mode="mode" @toggle="toggle"></novo-todo>
      </div>
      <div class="content">
        <todo-list :tarefas="tarefas" @check="checkTarefa" @remover="removerTarefa"></todo-list>
      </div>
    </div>
  </div>
</template>

<script>
import NovoTodo from './NovoTodo'
import TodoList from './TodoList'
import Toggle from './Toggle'
import App from '../App'

export default {
  name: 'todo-card',
  props: ['mode'],

  components: {
    NovoTodo,
    TodoList,
    Toggle
  },
  data () {
    return {
      dias: ['Domingo', 'Segunda', 'Terça', 'Quarta', 'Quinta', 'Sexta', 'Sábado'],
      meses: ['Janeiro', 'Fevereiro', 'Março', 'Abril', 'Maio', 'Junho', 'Julho', 'Agosto', 'Setembro', 'Outubro', 'Novembro', 'Dezembro'],
      tarefas: []
    }
  },
  computed: {
    hoje: function() {
      let novaData = new Date()
      return `${this.dias[novaData.getDay()]}, ${novaData.getDate()} de ${this.meses[novaData.getMonth()]}`
    }
  },
  methods: {
    adicionarTarefa(tarefa) {
      let nova_tarefa = {'description': tarefa, 'checked': false}
      this.tarefas.push(nova_tarefa)
    },
    checkTarefa(index) {
      this.tarefas[index]['checked'] = !this.tarefas[index]['checked']
    },
    removerTarefa(index){
      this.tarefas.splice(index,1)
    }
  }
}
</script>

<style>
.card {
  background-color: #f7f7f7;
  
  width: 400px;
  border-radius: 10px;
  box-shadow: 2px 2px 4px rgb(0, 0, 0, 0.1);
}

.content {
  display: flex;
  flex-flow: column;
  align-items: center;
}
.card-header-title {
  color: #636368;
  font-family: 'Comfortaa', cursive;
}

.card-header {
  box-shadow: none;
}

p.card-header-title {
  background-color: #c3bfc8;
  box-shadow: 0 0.5em 1em -0.125em rgba(10, 10, 10, 0.1);
}

p.card-header-title.has-text-left {
  box-shadow: 0 0.5em 1em -0.125em rgba(10, 10, 10, 0.1);
    background-color: #6388d2;
    color: white;
}
p.card-header-title.has-text-left.dark{
  background: #ff4c99;
}

</style>
