<template>
   <div>
      <nav class="footerbar">
         <div id="textbox">
            <p class="align-left navbar-item has-text-grey-light">Instant Share v0.0.1</p>
            <p class="align-right navbar-item" :style="`color:${color}`">{{ ping }}</p>
         </div>
      </nav>
   </div>
</template>
<script>
import WebSocket from 'ws'
const ws = new WebSocket('ws://localhost:8080/ping');

let pingms = 0;
let ping = "";
let color ="";


 
ws.on('message', function incoming(data) {
  console.log(data);
});

if(pingms>0){
     ping = `latency ${pingms}ms / block #0`;
    if(pingms < 60){
        color='green';
    } else {
        if( pingms > 60 && pingms < 100){
            color ="orange";
        } else {
            if(pingms < 300){
                color = "yellow";
            } else {
                if(pingms >= 300){
                    color = "red";
                }
            }
        }
    }
} else {
    color = "red";
    ping = "latency - / block #0"
}


export default {
    data(){
        return {
           color: color,
           ping: ping

        }
    }
}
</script>

<style scoped>
   .align-left {
   float: left;
   }
   .align-right {
   float: right;
   }
   .footerbar { 
   position: fixed !important; 
   left: 0; 
   right: 0; 
   bottom: 0;
   height: auto;
   background-color: #363636 !important;
   color: white;
   }
</style>