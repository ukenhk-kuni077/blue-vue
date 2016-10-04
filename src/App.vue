<template>
  <nav>
    <div>
      <h2 class="container">{{ msg }}</h1>
    </div>
  </nav>
  <div class="container">
      <task></task>
  </div>
  <div class="container">
    <a class="waves-effect waves-light btn">success</a>
    <a class="waves-effect waves-light btn">delete</a>
  </div>
  <div class="fixed-action-btn">
    <a class="btn-floating btn-large waves-effect waves-light red"><i class="material-icons">+</i>
      <modal v-bind:is-opened.sync="opened">
        <div class="modal-content">
          <h4>todo title</h4>
          <p>Detailed information</p>
          <div class="modal-footer">
            <div class="btn btn-flat" @click="close">cancel</div>
            <div class="btn btn-flat" @click="close">ok</div>
          </div>
        </div>
      </modal>
    </a>
  </div>
</template>

<script>
import Task from './Task.vue';
export default {
  data () {
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      msg: 'TODO',
      opened : false
    }
  },
  methods : {
    close (){
      console.log('click')
      this.opened = false;
    }
  },
  components:{
    Task,
    'modal' : require('vue-materialize/modal')
  }

}
</script>

<style>
body {
  font-family: Helvetica, sans-serif;
}
</style>
