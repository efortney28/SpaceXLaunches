<template>
  <div class="home">
    <Upcoming />
  </div>
</template>

<script>
// @ is an alias to /src
import Upcoming from '@/components/Upcoming.vue'

export default {
  name: 'home',
  components: {
    Upcoming,
  }
}
</script>
