<template>
  <div class="spiderCount">
      <h1>Welcome to the spiderman dashboard</h1>
      <b-table striped hover small dark :items="items" :fields="fields" ></b-table>
  </div>
</template>
<script>

import axios from 'axios';

export default {
  name: 'spiderCount',
  data() {
       return {
        sortable : true,
        fields : [{

            key : 'name',
            sortable : true
        },
        {

            
            key : 'spiderman_count',
            label : 'spiderman',
            sortable : true

        },
        {
            key : 'milesmorales_count',
            label : 'Miles Morales',
            sortable : true

        }],
        items: []
      }
  },
    async mounted(){

        
        let results = await axios.get(`${process.env.VUE_APP_SPIDERBOT}/users`);
       
        let names = results.data.map(x => x.name);
        

        let userProfileData = await Promise.all(names.map(async(name) => {

            let profileData = await axios.get(`${process.env.VUE_APP_SPIDERBOT}/users/${name}`);
            return profileData.data;

        }));
       
        this.items = userProfileData;

    }
}
</script>