<template>
     <section class="hero is-primary is-bold is-fullheight" :class="mode">

      <!-- Hero content: will be in the middle -->
      <div class="hero-body">
        <toggle :mode="mode" @toggle="toggle"></toggle>
        <div class="container has-text-centered">
          <div class="row">
            <div class="columns">
              <div class="column is-half is-offset-one-quarter">
                <todo-card :mode="mode" @toggle="toggle"></todo-card>
              </div>
            </div>
          </div>
        </div>
      </div>

    </section>
</template>

<script>
import TodoCard from './components/TodoCard'
import Toggle from './components/Toggle'
export default {
  name: 'app',
  components: {
    TodoCard,
    Toggle
  },
  data () {
    return {
      mode: "dark"
    }
  },
  methods: {
    toggle() {
      if (this.mode === "dark") {
        this.mode = ""
      } else {
        this.mode = "dark"
      }
    }
  }
}
</script>

<style>
.hero-body {
  flex-flow: column;
}
.hero.is-primary.is-bold {
  background-color: #e6e6e6;
  background-image: none;
}
.hero.is-primary.is-bold.dark {
  background:#17161b;
}
.container.has-text-centered {
  width: 100%;
  display: flex;
  place-content: center;
}
.column.is-half.is-offset-one-quarter {
  display: flex;
  justify-content: center;
  width: auto;
  margin: auto;
}
