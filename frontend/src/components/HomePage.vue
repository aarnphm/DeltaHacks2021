<template>
  <div id="HomePage">
    
    <h1> Greetings, {{username}} </h1>
    <h1>Help us identify which type of user you are: </h1>

    <div class="">
        <p class="intro"> Providing a carpool ride to other users is a good favor to other people while not harming any of your benefits. Our application will post your status online to allow other users to request.</p>
        <b-button class = "type" variant="primary"> Provide a carpool ride </b-button>   
        <p class="intro"> Requesting a carpool ride can be easy and convenient. This will grant you access to all the carpool drivers nearby your location. Wish you have a safe and happy ride.</p> 
        <b-button class = "type" variant="primary"> Request a carpool ride </b-button>
    </div>



  </div>
</template>

<script>

export default {
  name: 'HomePage',

  data(){
    return {
      
    }
  },

  methods: {
    provide(){

    },

    request(){

    }
  },

  beforeCreate(){
      this.username = this.$route.query.username;
  },


}
</script>

<style>

.type{
  width: 200px;
  height: 200px;
  background:paleturquoise
}

.intro{
  width: 400px;
  position: center;
  border: none;
  margin: auto;
}

</style>