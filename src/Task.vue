<template>
  <collapsible>
    <collapsible-item v-for="task in taskDatas" :task="task" track-by="$index">
      <h5 slot="header">
        <span @click.prevent="task.select = !task.select">
          <input type="checkbox" value="" v-model.sync="task.select"></input>
          <label></label>
        </span>
        {{ task.title }}
      </h5>
      <p>{{ task.body }}</p>
      <p>
        date : <input type="date" v-model.sync="task.date" length="10"></input>
        location : <select v-model.sync="task.location">
          <option>スーパー</option>
          <option>駅</option>
          <option>自宅</option>
        </select>
        category : <select v-model.sync="task.category">
          <option>shopping</option>
          <option>visit</option>
          <option>other</option>
        </select>
	  </p>
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
