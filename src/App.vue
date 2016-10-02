<template>
  <nav>
    <div>
      <h2 class="container">{{ msg }}</h1>
    </div>
  </nav>
  <div class="container">
    <collapsible>
      <collapsible-item>
        <h4 slot="header">
          <span @click="toggle1">
            <input type="checkbox" value="" v-model.sync="delete1"></input>
            <label></label>
          </span>
          Task1
        </h4>
        <p>body 1</p>
      </collapsible-item>
      <collapsible-item>
        <h4 slot="header">
          <span @click="toggle2">
            <input type="checkbox" value="" v-model.sync="delete2"></input>
            <label></label>
          </span>
          Task2
        </h4>
        <p>body 2</p>
      </collapsible-item>
    </collapsiSble>
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
export default {
  data () {
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      msg: 'TODO',
      opened : false,
      delete1 : false,
      delete2 : false
    }
  },
  methods : {
    toggle1 (e){
      this.delete1 = !this.delete1
      console.log(this.delete1);
      e.preventDefault()
    },
    toggle2 (e){
      this.delete2 = !this.delete2
      console.log(this.delete2);
      e.preventDefault()
    },
    close (){
      console.log('click')
      this.opened = false;
    }
  },
  components:{
    'collapsible' : require('vue-materialize/collapsible'),
    'collapsible-item' : require('vue-materialize/collapsible-item'),
    'modal' : require('vue-materialize/modal')
  }

}
</script>

<style>
body {
  font-family: Helvetica, sans-serif;
}
</style>
