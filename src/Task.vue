<template>
  <collapsible>
    <collapsible-item v-for="delete in task_deletes" :delte="delete" :index="$index">
      <h4 slot="header">
        <span @click="delete = !delete;e.preventDefault();">
          <input type="checkbox" value="" v-model.sync="delete"></input>
          <label></label>
        </span>
        Task1
      </h4>
      <p>body 1</p>
    </collapsible-item>
  </collapsiSble>
</template>

<script>
export default {
  data () {
    return {
      task_deletes : [false,false,false]
    }
  },
  components:{
    'collapsible' : require('vue-materialize/collapsible'),
    'collapsible-item' : require('vue-materialize/collapsible-item')
  }

}
</script>
