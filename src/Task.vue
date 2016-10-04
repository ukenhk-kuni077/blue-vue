<template>
  <collapsible>
    <collapsible-item v-for="task in taskDatas" :task="task" track-by="$index">
      <h5 slot="header">
        <span @click="delete = !delete;e.preventDefault();">
          <input type="checkbox" value="" v-model.sync="delete"></input>
          <label></label>
        </span>
        {{ task.title }}
      </h5>
      <p>{{ task.body }}</p>
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
