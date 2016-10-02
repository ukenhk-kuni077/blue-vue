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
            Task2</h4>
          </span>
        <p>body 2</p>
      </collapsible-item>
    </collapsible>
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
    }
  },
  components:{
    'collapsible' : require('vue-materialize/collapsible'),
    'collapsible-item' : require('vue-materialize/collapsible-item')
  }

}
</script>

<style>
body {
  font-family: Helvetica, sans-serif;
}
</style>
