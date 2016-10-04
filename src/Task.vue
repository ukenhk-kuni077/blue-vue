<template>
  <collapsible>
    <collapsible-item v-for="delete in taskDatas" :delete="delete" track-by="$index">
      <h5 slot="header">
        <span @click="delete = !delete;e.preventDefault();">
          <input type="checkbox" value="" v-model.sync="delete"></input>
          <label></label>
        </span>
        Task1
      </h5>
      <p>body 1</p>
    </collapsible-item>
  </collapsiSble>
</template>

<script>
export default {
  props : {
    taskDatas : Array
  },
  components:{
    'collapsible' : require('vue-materialize/collapsible'),
    'collapsible-item' : require('vue-materialize/collapsible-item')
  }

}
</script>
