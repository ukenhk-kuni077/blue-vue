<template>
  <div id="app">
    <h1>{{ msg }}</h1>
    <card class="sticky-action"> <!-- remove sticky-action class for normal action -->
      <img slot="img" src="http://materializecss.com/images/office.jpg"></img>
      <span slot="title">Title (click me)</span>
      <p>Some Content</p>
      <span slot="revealTitle">Title (click me)</span> <!-- required for reveal to work -->
      <p slot="reveal">Significantly more Content</p>
      <a slot="action" href="#card">Some sticky action</a>
    </card>
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
      msg: 'Hello Vue!'
    }
  },
  components:{
    'card': require('vue-materialize/card')
  }

}
</script>

<style>
body {
  font-family: Helvetica, sans-serif;
}
</style>
