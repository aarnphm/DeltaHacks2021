<template>
  
  <div id="RequestPage">
    <b-navbar type = "Light" variant="faded">
      <b-navbar-brand href="#">
        <img src="../assets/taxiwhite.png" class="logo" alt="logo">
        Karlpol
      </b-navbar-brand>
    </b-navbar>

    <MapPage/>

    <div class="filter">
        <h2 class = "filter-text"> Where are you going? </h2>
        <b-form @submit.prevent="find" class="filter_form">
            
            <b-form-group id = "input-g1" label = "Starting Address" label-for = "start_address">
              <b-form-input
                id = "input-1" 
                type="text" 
                name="start_address" 
                v-model="start_address" 
                placeholder="Current location" 
                required
              >
              </b-form-input>
            </b-form-group>

            <b-form-group id = "input-g2" label = "Destination" label-for = "Destination">
              <b-form-input
                id = "input-2" 
                type="text" 
                name="destination" 
                v-model="destination" 
                placeholder="Search" 
                required
              >
              </b-form-input>
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

        </b-form>
    </div>
    

  </div>
</template>

<script>

import MapPage from "./MapPage"


export default {
    name: 'RequestPage',

    components: {
        MapPage
    },

    data(){
        return {
            start_address: null,
            destination: null,
            radius: null,
            date: null,
            location: '36 Hollywood North, Hamilton, ON',
        }
    },

    methods: {

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
  MglMarker{
    margin:0;
    max-width:none;
    height : none;
  }

  MglNavigationControl{
    width : 100px;
  }

</style>