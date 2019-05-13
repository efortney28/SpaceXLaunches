<template>
<div>
  <div v-for="(launch, index) in launches" :key='index' class="card">
      <div class="row">
        <div class="col-sm-12">
          <div class="card-body">
            <img v-if="launch.links.mission_patch_small" class="card-img-right patch" :src="launch.links.mission_patch_small" alt="Mission Patch">
            <span v-else class="patch">Patch Not Available</span>
            <h2>{{ launch.mission_name}}</h2>
            <p>{{ launch.details }}</p>
            <p> Launching from {{ launch.launch_site.site_name}} on {{launch.launch_date_local | momentDate}} at {{launch.launch_date_local | momentTime}}.</p>
            <p v-if="launch.rocket.first_stage.cores[0].block">Block Number: {{ launch.rocket.first_stage.cores[0].block}}</p>
            <p v-else>Block: N/A</p>
            <p v-if="launch.rocket.first_stage.cores[0].core_serial">Core Serial: {{ launch.rocket.first_stage.cores[0].core_serial }}</p>
            <p v-else>Core Serial: N/A</p>
            <p v-if="launch.rocket.second_stage.payloads[0].orbit === 'LEO'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Low Earth Orbit)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'MEO'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Medium Earth Orbit)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'HEO'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (High Earth Orbit)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'ISS'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (International Space Station)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'SO'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Sub-Orbital)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'SSO'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Sun-Synchronous Orbit)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'TLI'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Trans-Lunar Injection)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'GTO'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Geostationary Transfer Orbit)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'PO'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Polar Orbit)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'ES-L1'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Lagrange Point 1)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'ES-L2'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Lagrange Point 2)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'ES-L3'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Lagrange Point 3)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'ES-L4'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Lagrange Point 4)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'ES-L5'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Lagrange Point 5)</p>
            <p v-else-if="launch.rocket.second_stage.payloads[0].orbit === 'HCO'">Orbit: {{ launch.rocket.second_stage.payloads[0].orbit }} (Heliocentric Orbit)</p>
          </div>
        </div>
      </div>
  </div>
</div>
</template>

<script>
import axios from 'axios'
import moment from 'moment'

export default {
  name: 'upcoming',
  data() {
    return {
      launches: null,
      errors: [],
    }
  },
  async created() {
    try {
      const res = await axios.get('https://api.spacexdata.com/v3/launches/upcoming')
      this.launches = res.data
      console.log(this.launches)
    } catch (e) {
      this.errors.push(e)
      console.log(this.errors)
    }
  },
  filters: {
    momentDate: function(val) {
      return moment(val).format('MMMM Do, YYYY')
    },
    momentTime: function(val) {
      return moment(val).format('h:mm:ss a')
    }
  },
  methods: {

  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
