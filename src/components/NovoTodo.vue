
<template>
  <div class="row">
    <div class="columns">
      <div class="column  is-half is-offset-one-quarter">
        <div class="field is-grouped">
          <p class="control is-expanded">
             <input class="input is-primary has-text-centered" type="text" placeholder="Nova tarefa..." v-model="tarefa">
          </p>
          <p class="control">
            <a class="button is-success add-button" @click="enviarTarefa" :class="mode">
              <span class="icon is-small">
                <i class="fa fa-plus"></i>
              </span>
            </a>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>



export default {
  name: 'novo-todo',
  props: ['mode'],
  data () {
    return {
      tarefa: ''
    }
  },
  methods : {
    enviarTarefa(tarefa) {
      if (this.tarefa != '') {
        this.$emit('novaTarefa', this.tarefa)
      }
      this.tarefa = ''
    }
  }
}
</script>

<style>

.row {
  display: flex;
}

.input {
  border-left: 0;
  border-right: 0;
  border-top: 0;
  border-radius: 0;
  outline: none;
  border-bottom-width: 2px;
  box-shadow: none;
}

.input.is-primary{
  background-color: transparent;
  border-color: #e6e6e6;
  font-family: 'Montserrat', sans-serif;

  transition: 200ms;
}

.input.is-primary:focus {
  box-shadow: none;
  border-color: rgb(168, 168, 168);
}
.add-button {
  border-radius: 50%;
  box-shadow: 2px 2px 4px rgb(0, 0, 0, 0.1), -2px -2px 6px white;
}

.button.is-success {
  background-color:#6388d2;
}
.button.is-success:hover {
  background-color:#6388d2;
}

.button.is-success.dark {
  background-color:#ff4c99;
}

</style>
