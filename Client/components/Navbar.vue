<template>
   <div class="hero-head has-text-white ">
      <nav class="navbar is-dark dark">
         <div class="navbar-brand">
            <nuxt-link class="navbar-item" to="/">Dashboard</nuxt-link>
            <nuxt-link class="navbar-item light-text" to="/deposit-withdraw">Deposit/Withdraw</nuxt-link>
            <div class="navbar-burger " @click="showNav = !showNav" :class="{ 'is-active': showNav }">
               <span></span>
               <span></span>
               <span></span>
            </div>
         </div>
         <div class="navbar-menu has-background-dark" :class="{ 'is-active': showNav }">
            <div class="navbar-end">
               <div class="navbar-item has-dropdown is-hoverable" v-if="isAuthenticated">
                  <a class="navbar-link light-text" disabled>
                  {{ loggedInUser.username }}
                  </a>
                  <div class="navbar-dropdown has-background-dark">
                     <nuxt-link class="navbar-item light-text" to="/profile">My Profile</nuxt-link>
                     <nuxt-link class="navbar-item light-text" to="/dashboard" v-if="loggedInUser.is_admin==1">Dashboard</nuxt-link>
                     <a class="navbar-item has-text-white" @click="logout">Logout</a>
                  </div>
               </div>
               <template v-else>
                  <nuxt-link class="navbar-item" to="/register">Register</nuxt-link>
                  <nuxt-link class="navbar-item" to="/login">Log In</nuxt-link>
               </template>
            </div>
         </div>
      </nav>
   </div>
</template>
<script>
   import { mapGetters } from 'vuex'
   
   export default {
   data: function() {
     return{
       showNav: false
     }
     },
   methods: {
     async logout() {
       await this.$auth.logout();
     },
   },
     computed: {
       ...mapGetters(['isAuthenticated', 'loggedInUser','isAdmin'])
     }
   }
</script>
<style scoped>
   .nuxt-link-exact-active{
   background-color: #212121;
   pointer-events: none;
   }
   .navbar-item:hover{
   color: black;
   }
   .light-text{
   color: white;
   }
   .navbar { 
   position: fixed !important; 
   top: 0; 
   left: 0; 
   right: 0; 
   }
</style>