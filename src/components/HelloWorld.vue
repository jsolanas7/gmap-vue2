<template>
  <div>
    <h1>Ingrese coordenadas</h1>
  <input type="text" v-model="latitude" placeholder="Latitud"/>
  <input type="text" v-model="longitude" placeholder="Longitud"/>
  <button v-on:click="handleSearch()">Buscar</button>
  <GmapMap
    ref="mapRef"
    :center="center"
    :zoom="15"
    map-type-id="terrain"
    style="width: 100vw; height: 100vh"
  >
    <GmapMarker
      :key="index"
      v-for="(m, index) in locations"
      :position="m"
    />
  </GmapMap>
  </div>
</template>

<script>
import {gmapApi} from 'vue2-google-maps'
export default {
  data () { return {
      latitude: '-33.8934279',
      longitude: '-61.1053805',
      center: {
        lat: 41.3828939,
              lng: 2.1774322,
      },
     locations : [
          {
              lat: 39.7837304,
              lng: -100.4458825,
              label: 'United States'
          },
          {
              lat: 38.6529545,
              lng: -90.2411166,
              label: 'St. Louis'
          },
          {
              lat: 41.3828939,
              lng: 2.1774322,
              label: 'Barcelona'
          },
          {
              lat: -10.3333333,
              lng: -53.2,
              label: 'Brazil'
          }
      ]
  }
  },
  name: 'HelloWorld',
  props: {
    msg: String
  },
  computed: {
    google: gmapApi
  },
  methods: {
    handleSearch(){
      // eslint-disable-next-line
      debugger;
      if(this.latitude && this.longitude){
        this.locations = [];
        this.locations.push({
          lat: parseFloat(this.latitude),
          lng: parseFloat(this.longitude),
          label: ''
        });
        this.center = {
          lat: parseFloat(this.latitude),
          lng: parseFloat(this.longitude),
        }
        
      }else{
        alert('Debe ingresar longitud y latitud');
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
