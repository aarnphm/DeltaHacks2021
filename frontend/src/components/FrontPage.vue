<template>
  <div id="FrontPage">
    <b-navbar fixed = "top" sticky = true type = "light" variant="faded">
      <b-navbar-brand href="#" tag = "nav_title"><span class="mb-0 h1">
        Karlpol</span>
      </b-navbar-brand>
    </b-navbar>
        <b-card bg-variant="light" v-show="show" class="covid_notice">
          <div>
            <h2>CoronaVirus (COVID-19) </h2>
            <p>Help protect yourself and others.</p>
            <p>No masks. No ride.</p>
            <b-button variant="primary" v-on:click="show = false">I am aware.</b-button>
          </div>
        </b-card>
        <b-card class = "front_img" overlay v-bind:img-src = "require('../assets/covid_carsharing.png')" img-alt="Card image" img-bottom title = "Share your journeys." title-tag ='h1'> 
        </b-card>
        

          
        <b-card class = "login_section">
          <h2> Pool it. </h2>
          <b-form @submit.prevent="login" class = "login_form">

            <b-form-group id = "input-g1" label = "Username" label-for = "Username">
              <b-form-input
                id = "input-1" 
                type="text" 
                name="username" 
                v-model="username" 
                placeholder="Enter username" 
                required
              >
              </b-form-input>
            </b-form-group>

            <b-form-group id = "input-g2" label = "Password" label-for = "Password">
              <b-form-input 
                id = "input-2" 
                type="text" 
                name="password" 
                v-model="password" 
                placeholder="Enter password" 
                required
              >
              </b-form-input>
            </b-form-group> 
            <p v-if="feedback" class="fb">{{ feedback }}</p>
            <b-button type="submit" variant="primary" class="button">Start</b-button>
          </b-form>
          <a href="/#/signup">Don't have an account? Sign up today!</a>
        </b-card>

        <div> AMMK @ Deltahacks 2021</div>
      </div>

</template>

<script>

export default {
  name: 'FrontPage',

  data(){
    return {
      username: null,
      password: null,
      feedback: null,
      show: true,
    }
  },

  methods: {
    login(){
        //authenticate
        const auth = true;
        if (auth){
          this.$router.push("./homepage")
        }else{
          this.feedback = "Incorrect username or password."
        }

    },

  }

}
</script>

<style scoped>
  .card {
    background: white
  }
  .front_img{
    position: center;
    border: none;
    margin-left: auto;
    margin-right: auto;
    width: 100%;
    max-width: 600px;
  }
  .login_form{
    margin-left: auto;
    margin-right: auto;
    width: 100%;
    max-width: 240px;
  }
  .login_section{
    background: rgba(216, 227, 255, 0.41);
    margin-left: auto;
    margin-right: auto;
    width: 100%;
  }

  .navbar {
    background: #5B7BBA;
  }

  .navbar-light .navbar-brand{
    font-size: x-large;
    font-style: normal;
    font-weight: bolder;
    font-size: 40px;
    line-height: 42px;

    color: white;
    
  }

  .frontpage{
    position: relative;
    margin: 0;
    padding-top: 0px;

  }

</style>