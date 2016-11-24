<template>
  <nav>
    <div>
      <h2 class="container">spot select</h1>
    </div>
  </nav>
  <div class="container">
    <map
      :center.sync="mapCenter"
      :zoom.sync="zoom">
      <marker :position.sync="mapCenter">
      </marker>
      <circle :center.sync="mapCenter" :radius.sync="100" :options="{editable: true}"></circle>
    </map>
    <div class="row"></div>
    <div class="row">
      <a class="col offset-s4 s4 waves-effect waves-light btn" @click="registration">Registration</a>
    </div>
  </div>
</template>

<script>
import {load, Map, Marker, InfoWindow, Circle} from 'vue-google-maps'
import config from '../config/config'
load(config.gmap);

export default {
  route : {
    data ({ next }){
      navigator.geolocation.getCurrentPosition(pos=>{
        this.mapCenter.lat = pos.coords.latitude;
        this.mapCenter.lng = pos.coords.longitude;

        this.taskData = JSON.parse(sessionStorage.getItem('select_task')) || {};

        let locations = this.taskData.todoLocation || {};

        next();
      });
    }
  },
  data () {
    return {
      mapCenter : { lat: 35.698487083032546, lng: 139.77340467619624 },
      zoom : 15,
      markers: [],
      taskData : {}
    }
  },
  methods : {
    registration (){
      let task = JSON.parse(sessionStorage.getItem('select_task'));
      Object.assign(task,{
        todoLocation : {
          name : task.name,
          latitude : this.mapCenter.lat,
          longitude : this.mapCenter.lng
        }
      });
      sessionStorage.setItem('select_task',JSON.stringify(task));
      this.$route.router.go({ path:'/' });
    }
  },
  components : { Map, Marker, InfoWindow, Circle }
}
</script>

<style>
map {
  width:100%;
  height: 75vh;
  display: block;
}
</style>
