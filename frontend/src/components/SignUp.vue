<template>
  <div id="SignUp">
    <h1>Sign Up With Karlpol</h1>
    <div class = "card"> 
        <form @submit.prevent="signup">
            <label for="name"> Enter your name:  </label>
            <input type="text" name="name" v-model="name" placeholder="Enter here">
            <label for="username"> Enter a username:  </label>
            <input type="text" name="username" v-model="username" placeholder="Enter here">
            <label for="password"> Enter a password:  </label>
            <input type="text" name="password" v-model="password" placeholder="Enter here">
            <label for="email"> Enter your email:  </label>
            <input type="text" name="email" v-model="email" placeholder="Enter here">
            <p v-if="feedback" class="fb">{{ feedback }}</p>
            <button class="button">Sign Up Today!</button>
        </form>
    </div>
  </div>
</template>

<script>

export default {
  name: 'SignUp',
  data(){
    return {
      username: null,
      password: null,
      name: null,
      email: null
    }
  },

  methods: {
    signup(){
      //register in the database
    }
  }
}
</script>

<style>

</style>