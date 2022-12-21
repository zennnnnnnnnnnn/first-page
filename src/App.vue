<template>
  <div>
    <p>Your IP address is {{ ip }}</p>
    <p>Your location is {{ location }}</p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      ip: '',
      location: '',
    };
  },
  created() {
    axios.get('http://ip-api.com/json')
      .then((response) => {
        this.ip = response.data.query;
        this.location = `${response.data.city}, ${response.data.country}`;
      });
  },
};
</script>
