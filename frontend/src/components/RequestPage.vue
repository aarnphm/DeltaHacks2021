<template>
  <div id="RequestPage">
    <div class="filter">
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

            <b-form-group id = "input-g3" label = "Radius of searching (in km)" label-for = "Radius">
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
              <b-form-input class="textInput" type="text" id="textInput" value="">
              </b-form-input>
            </b-form-group>

        </b-form>
    </div>

  </div>
</template>

<script>

export default {
    name: 'MapPage',

    data(){
        return {
            start_address: null,
            destination: null,
            radius: null

        }
    },

    methods: {

    },


}
</script>

<style>

.textInput{
    text-align: center;
    
}

</style>