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
      <div class="container">
        <div class="row"></div>
        <div class="row">
          <div class="col s12">
          {{ task.body }}
          </div>
        </div>
        <div class="row">
          <a class="col offset-s9 s3 waves-effect waves-light btn" @click="geoRegistration(task)">geopos</a>
        </div>
        <div class="row">
          <input-field class="col s12" type="date" :value.sync="task.regDate" label="date : "></input-field>
        </div>
        <div class="row">
          <div class="col s12">
            <label>location : </label>
            <select :value.sync="task.location" class="browser-default">
              <option v-for="location in locations" :value="location.value" v-text="location.value"></option>
            </select>
          </div>
        </div>
        <div class="row">
          <div class="col s12">
            <label>category : </label>
            <select :value.sync="task.category" class="browser-default">
              <option v-for="category in categories" :value="category.value" v-text="category.value"></option>
            </select>
          </div>
        </div>
      </div>
    </collapsible-item>
  </collapsiSble>
</template>

<script>
export default {
  data () {
    return {
      locations : [
        {value:'super',  text:'スーパー'},
        {value:'station',text:'駅'},
        {value:'home',   text:'自宅'}
       ],
      categories : [
        {value:'shopping', text:'shopping'},
        {value:'visit',    text:'visit'},
        {value:'other',    text:'other'}
       ]
      }
  },
  props : {
    taskDatas : Array
  },
  methods : {
    geoRegistration (task){
      sessionStorage.setItem('select_task',JSON.stringify(task));
      this.$route.router.go({ name:'Map', params: { task_id : task._id } });
    }
  },
  components:{
    'input-field' : require('vue-materialize/input-field'),
    'collapsible' : require('vue-materialize/collapsible'),
    'collapsible-item' : require('vue-materialize/collapsible-item')
  }
}
</script>
