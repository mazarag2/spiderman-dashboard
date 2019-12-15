<template>
  <div class="spiderEvents">
      <h2>View Indiviual Events by User</h2>
       <b-button v-for="(user, index) in users" v-bind:key="index" v-b-toggle.collapse-1 variant="primary">{{user}}</b-button>
        <b-collapse id="collapse-1" class="mt-2">
        <b-card>
            <p class="card-text">Events</p>
        </b-card>
      </b-collapse>
  </div>
</template>
<script>

import axios from 'axios';

export default {
  name: 'spiderEvents',
  data(){

      return {

          users : []

      }

  },
  async mounted(){

        let results = await axios.get(`${process.env.VUE_APP_SPIDERBOT}/users`);
       
        let names = results.data.map(x => x.name);
        console.log(names);
        this.users = names;
        
  }
}
</script>