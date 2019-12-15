<template>
  <div class="SpiderEvent">
      <b-list-group>
       <b-list-group-item variant="light" v-for="event in events" v-bind:key="event.uuid">
         Date : {{ event.dateposted }} , Message : {{ event.msg }} 
       </b-list-group-item>
      </b-list-group>
  </div>
</template>
<script>

import axios from 'axios';

export default {
  name: 'SpiderEvent',
  props : ['username'],
  data(){
   return {
     events : [],
     convertTimeStampToDate : (event) => {

       let date = new Date(event.dateposted);
       return date.toDateString();

     }
   }

  },
  async mounted(){

        let results = await axios.get(`${process.env.VUE_APP_SPIDERBOT}/users/${this.username}/events`);
        results = results.data;
        results.map((event) => {

          let convertedTime = this.convertTimeStampToDate(event);
          console.log(convertedTime);
          event.dateposted = convertedTime;

        })
        console.log(results);
        this.events = results;
  }
}
</script>