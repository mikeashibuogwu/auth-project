<template>
    <div id="nav">
      <router-link style="text-decoration:none;" to="/">Home</router-link> |
      <router-link style="text-decoration:none;" to="/products">Products</router-link> |
      <span v-if="isLoggedIn">
        <a @click="logout">Logout</a>
      </span>
      <span v-else>
        <router-link style="text-decoration:none;" to="/signup">Sign Up</router-link> |
        <router-link style="text-decoration:none;" to="/login">Log In</router-link>
      </span>
    </div>
  </template>
  <script>
  export default {
    name: 'NavBar',
    computed : {
        isLoggedIn : function(){ return this.$store.getters.isAuthenticated}
      },
      methods: {
        async logout (){
          await this.$store.dispatch('LogOut')
          this.$router.push('/login')
        }
      },
  }
  </script>
  <style>
  #nav {
    padding: 30px;
  }
  #nav a {
    font-weight: bold;
    color: #2c3e50;
  }
  a:hover {
    cursor: pointer;
  }
  #nav a.router-link-exact-active {
    color: #42b983;
  }
  </style>
  