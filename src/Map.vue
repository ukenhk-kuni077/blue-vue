<template>
  <nav>
    <div>
      <h2 class="container">spot select</h1>
    </div>
  </nav>
  <div class="container">
    <map
      :center.sync="center"
      :zoom.sync="zoom"
      @g-click="mapClick">
      <marker 
        v-for="m in markers"
        :position.sync="m.position">
        <info-window
          :opened.sync="m.open"
          :content="m.content"></info-window>
      </marker>
    </map>
    <div class="row"></div>
    <div class="row" v-show='selectedSpot'>
      <a class="col offset-s4 s4 waves-effect waves-light btn" @click="registration">Registration</a>
    </div>
  </div>
</template>

<script>
import {load, Map, Marker, InfoWindow} from 'vue-google-maps'
import config from '../config/config'
load(config.gmap);

export default {
  ready (){
    navigator.geolocation.getCurrentPosition(pos=>{
      this.center = {lat: pos.coords.latitude, lng: pos.coords.longitude};
      this.markers.push({
        position :{
          lat: pos.coords.latitude,
          lng: pos.coords.longitude,
        },
        content: 'now this position',
        open : true
      });
    });
  },
  watch : {
    canter (){ console.log(this.center)}
  },
  data () {
    return {
      center: {lat: 10.0, lng: 10.0},
      zoom : 15,
      markers: []
    }
  },
  computed : {
     selectedSpot (){
      return this.markers.length >= 2;
    }
  },
  methods : {
    mapClick (mouseArgs){
      this.markers.$set( 1,{
        position :{
          lat: mouseArgs.latLng.lat(),
          lng: mouseArgs.latLng.lng(),
        },
        content: 'select this?',
        open : true
      });
    },
    registration (){
      let task = JSON.parse(sessionStorage.getItem('select_task'));
      Object.assign(task,{
        todoLocation : {
          name : task.name,
          latitude : this.markers[1].lat,
          longitude : this.markers[1].lng
        }
      });
      sessionStorage.setItem('select_task',JSON.stringify(task));
      this.$route.router.go({ path:'/' });
    }
  },
  components : { Map, Marker, InfoWindow}
}
</script>

<style>
map {
  width:100%;
  height: 600px;
  display: block;
}
</style>
