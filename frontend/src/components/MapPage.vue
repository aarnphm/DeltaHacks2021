<template>
    <div>
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

 export default{
    components: {
        MglMap,  
        MglNavigationControl,
        MglGeolocateControl,
        MglMarker
    },

    data(){
        return {
            accessToken: 'pk.eyJ1IjoibWFybG9uNGRhc2hlbiIsImEiOiJja2x5OXh6b2MzaHUxMm9tcGswNDQ5Mjl5In0.ToKpQYWEXcexzrlmLpDDdQ', // your access token. Needed if you using Mapbox maps
            mapStyle: 'mapbox://styles/mapbox/streets-v11', // your map style
            coordinates: [-40, 10],
        
        }
    },

    created() {
    // We need to set mapbox-gl library here in order to use it in template
        this.mapbox = Mapbox;
    }

 }
</script>

<style>

</style>