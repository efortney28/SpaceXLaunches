<template>
    <div>
        <div v-for="(launch, index) in launches" :key='index'>
        <h2>{{ launch.mission_name}}</h2>
        <p>{{ launch.details }}</p>
        <p> Launched from {{ launch.launch_site.site_name}} on {{launch.launch_date_local | momentDate}} at {{launch.launch_date_local | momentTime}}.</p>
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
        const res = await axios.get('https://api.spacexdata.com/v3/launches/past')
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

<style>

</style>
