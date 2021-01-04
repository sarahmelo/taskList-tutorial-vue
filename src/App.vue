<template>
  <div id="app">
     <section class="hero is-primary is-bold is-fullheight">

      <!-- Hero content: will be in the middle -->
      <div class="hero-body">
        <div class="container has-text-centered">
          <div class="row">
            <div class="columns">
              <div class="column is-half is-offset-one-quarter">
                <todo-card></todo-card>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Hero footer: will stick at the bottom -->
      <div class="hero-foot">
        <div class="container">
          <div class="content has-text-centered">
            <p>
            </p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import TodoCard from './components/TodoCard'
export default {
  name: 'app',
  components: {
    TodoCard
  },
  data () {
    return {
      msg: 'Hello, World!'
    }
  }
}
</script>

<style>

.hero.is-primary.is-bold {
  background-color: #e6e6e6;
  background-image: none;
}

</style>