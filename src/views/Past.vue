<template>
  <div class="past">
    <Previous />
  </div>
</template>

<script>
// @ is an alias to /src
import Previous from '@/components/Previous.vue'

export default {
  name: 'past',
  components: {
    Previous,
  }
}
</script>