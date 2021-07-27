<template>

  <main v-if="!loading">
      <div class="text-1xl mt-4 mb-5 text-center text-gray-500">
          Información recuperada: {{ dataDate }}
      </div>
    <Stats :titulo="'Colombia'" :stats="statsCo"/>
    <Graphs />
    <br>
    <br>
    <Stats :titulo="'Global'" :stats="statsG"/>
  </main>

  <main v-else class="flex flex-col align-center justify-center text-center">
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Cargando Información
    </div>
    <img :src="loadingImg" alt="Cargando.." class="w-24 m-auto">
  </main>

</template>

<script>
import moment from 'moment'
import Stats from '../components/Stats.vue'
import Graphs from '../components/Graphs.vue'

export default {
  name: 'Home',
  components: {
    Stats,
    Graphs,
  },
  data(){
    return {
      loading: true,
      dataDate: '',
      statsG: {},
      statsCo: {},
      loadingImg: require("../assets/hourglass.gif")
    }
  },
  methods: {
    async llamadaAPI(){
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    },
    async llamadaLive(){
      const res = await fetch('https://api.covid19api.com/live/country/colombia')
      const data = await res.json()
      return data
    },
  },
  async created(){
    const data = await this.llamadaAPI()
    this.dataDate = moment(data.Date).locale('es').format('Do MMMM YYYY, h:mm:ss a') //Fecha del llamado formateada
    this.statsG = data.Global // Resumen global
    this.statsCo = data.Countries[36] //Resumen Colombia

    console.log(this.statsCo);
    
    //console.log(await this.llamadaLive());

    this.loading = false;
  }
}
</script>
