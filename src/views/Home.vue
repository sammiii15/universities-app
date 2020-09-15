<template>
  <div class="home">
    <universities/>
  </div>
</template>

<script>
// @ is an alias to /src
import universities from '@/components/universities.vue'

export default {
  name: 'Home',
  components: {
    universities
  }
}
</script>

