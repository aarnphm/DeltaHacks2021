<template>
  
  <div id="RequestPage">

    <div class="filter">
        <h2> To narrow down the options for your carpool, our app needs you to provide the following information: </h2>
        <b-form @submit.prevent="find" class="filter_form">
            
            <b-form-group id = "input-g1" label = "Starting Address" label-for = "start_address">
              <b-form-input
                id = "input-1" 
                type="text" 
                name="start_address" 
                v-model="start_address" 
                placeholder="Enter starting address" 
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
                placeholder="Enter your destination" 
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

        </b-form>
    </div>
    <MglMap :accessToken="accessToken" :mapStyle="mapStyle" :center="coordinates">
        <MglMarker :coordinates="coordinates" color="blue" />
        <MglNavigationControl position="top-right" />
        <MglGeolocateControl position="top-right" />
        
    </MglMap>
  </div>
</template>

<script>
import Mapbox from "mapbox-gl";
import { MglMap,  MglNavigationControl, MglGeolocateControl, MglMarker } from "vue-mapbox";



export default {
    name: 'RequestPage',
    components: {
        MglMap,  
        MglNavigationControl,
        MglGeolocateControl,
        MglMarker
    },
    data(){
        return {
            start_address: null,
            destination: null,
            radius: null,
            accessToken: 'pk.eyJ1IjoibWFybG9uNGRhc2hlbiIsImEiOiJja2x5OXh6b2MzaHUxMm9tcGswNDQ5Mjl5In0.ToKpQYWEXcexzrlmLpDDdQ', // your access token. Needed if you using Mapbox maps
            mapStyle: 'mapbox://styles/mapbox/streets-v11', // your map style
            coordinates: [-40, 10],
        
        }
    },

    methods: {

    },

    created() {
    // We need to set mapbox-gl library here in order to use it in template
        this.mapbox = Mapbox;
    }
}
</script>

<style>

.textInput{
    text-align: center;

}

</style>