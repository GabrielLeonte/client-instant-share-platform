<template>
   <section class="container light-text is-pulled-left ">

<div class="columns is-multiline" style="padding-top: 60px;" >
    <div class="column is-one-quarter" v-for="(item,i) in coins" :key="`${i}-${item}`">
      {{ item.coin }} 
    </div>
  </div>

   </section>
</template>
<style scoped>
@import url('https://fonts.googleapis.com/css?family=Poppins');
   body{
   background-color: #212121;
   }
   .light-text{
   color: white;
   }
</style>



<script>
   export default {
   async asyncData({ $axios }) {
   const coins = await $axios.$post('/me/coins')
   return { coins }
   }
   
   }
</script>