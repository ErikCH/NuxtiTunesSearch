<template>
  <div>
    <h1>Hello From results route {{$route.params.id}}</h1>
    <h2> output</h2>
    {{albumData}}
  </div>
</template>
<script>
import axios from 'axios';
export default {
  asyncData({params}) {
    return axios.get(`https://itunes.apple.com/search?term=${params.id}&entity=album`)
      .then((response) => {
        return {albumData: response.data.results}
      });
  },
  middleware: 'search'

}
</script>
