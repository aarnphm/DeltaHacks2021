<template>
  
  <div id="RequestPage">
    <b-navbar type = "Light" variant="faded">
      <b-navbar-brand href="#">
        <img src="../assets/taxiwhite.png" class="logo" alt="logo">
        Karlpol
      </b-navbar-brand>
    </b-navbar>

    <gmap-map
      :center="center"
      :zoom="12"
      style="width:100%;  height: 400px;"
    >
      <gmap-marker
        :key="index"
        v-for="(m, index) in markers"
        :position="m.position"
        @click="center=m.position"
      ></gmap-marker>
    </gmap-map>

    <div class="filter">
        <h2 class = "filter-text"> Where are you going? </h2>
        <b-form @submit.prevent="find" class="filter_form">
            
            <b-form-group id = "input-g1" label = "Starting Address" label-for = "start_address">
              <gmap-autocomplete :value="start_address"></gmap-autocomplete>
            </b-form-group>

            <b-form-group id = "input-g2" label = "Destination" label-for = "Destination">
              <gmap-autocomplete :value="destination"></gmap-autocomplete>
            </b-form-group>

            <b-form-group id = "input-g3" label = "Radius of Searching (in km)" label-for = "Radius">
              <b-form-input
                id = "input-3" 
                type="range" 
                name="radius"
                min="5"
                max="20" 
                v-model="radius" 
                onChange="document.getElementById('textInput').value = this.value"
                required
              >
              </b-form-input>
              <b-form-input class="textInput" type="text" id="textInput" value="13" disabled>
              </b-form-input>
            </b-form-group>

            <b-form-group id = "input-g4" label = "Date" label-for = "date">
              <b-form-input
                id = "input-4" 
                type="date" 
                name="date"
                v-model="date" 
                required
              >
              </b-form-input>
            </b-form-group>
            <div>
              Provide information to narrow down your carpool options.
            </div>

            <b-button type="submit" v-on:click="find_match" variant="primary" class="button">  Submit </b-button>

        </b-form>
    </div>
    

  </div>
</template>

<script>



export default {
    name: 'RequestPage',

    data(){
        return {
            start_address: null,
            destination: null,
            radius: null,
            date: null,
        }
    },

    methods: {
        find_match(){

            
        },

        geolocate: function() {
        navigator.geolocation.getCurrentPosition(position => {
        const lati = position.coords.latitude;
        const long = position.coords.longitude;
        this.center = {
          lat: lati,
          lng: long
        };
        const marker = {
          lat: lati,
          lng: long
        };
        this.markers.push({ position: marker});
      });

    }
    },

    mounted() {
    this.geolocate();
  },

}
</script>

<style scoped>


  .navbar {
    background: #5B7BBA;
  }
  .logo{
    border: none;
    margin-left: auto;
    margin-right: auto;
    width: 45px;
  }
  .navbar-Light .navbar-brand{

    color: white;
    font-style: normal;
    font-weight: bolder;
    font-size: 40px;
    line-height: 42px;

  }

  .filter_form{
    margin-left: auto;
    margin-right: auto;
    width: 100%;
    max-width: 240px;
    padding: 10px;
  }
  .filter-text{
    margin-top: 50px;
    padding: 10px;
  }
  .filter{
    background: rgba(216, 227, 255, 0.41);
    margin-left: auto;
    margin-right: auto;
    width: 100%;
    padding: 10px;
  }
  .button{
      margin-top: 20px;
  }

</style>