<template>
  <nav>
    <div>
      <h2 class="container">{{ msg }}</h1>
    </div>
  </nav>
  <div class="container">
    <task :task-datas="taskDatas"></task>
  </div>
  <div class="container">
    <a class="waves-effect waves-light btn">success
      <modal>
        <div class="modal-content">
          <h4>success</h4>
          <p>Detailed information</p>
          <div class="modal-footer">
            <div class="btn btn-flat">cancel</div>
            <div class="btn btn-flat">ok</div>
          </div>
        </div>
      </modal>
    </a>
    <a class="waves-effect waves-light btn">delete</a>
  </div>
  <div class="fixed-action-btn">
    <a class="btn-floating btn-large waves-effect waves-light red"><i class="material-icons">add</i>
      <modal v-bind:is-opened.sync="opened">
        <div class="modal-content">
          <div class="row">
            <div class="input-field">
              <input type="text" v-model="taskTitle">
              <label>task title</label>
            </div>
            <div class="input-field">
              <input type="text" v-model="taskBody">
              <label>Detailed information</label>
            </div>
          </div>
          <div class="modal-footer">
            <div class="btn btn-flat" @click="close">cancel</div>
            <div class="btn btn-flat" @click="addTask">ok</div>
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
      opened : false,
      taskDatas : [
        {title:'task1', body:"body1",select:false},
        {title:'task2', body:"body2",select:false},
      ],
      taskTitle : '',
      taskBody : ''
    }
  },
  methods : {
    addTask (){
      this.taskDatas.push({
        title:this.taskTitle,
        body:this.taskBody,
        select:false
      });
      this.taskTitle = '';
      this.taskBody = '';
      this.opened = false;
    },
    close (){
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
