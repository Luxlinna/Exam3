<template>
  <div class="home justify-content-center">  
    <HomePage/>
  </div>
</template>

<script>
// @ is an alias to /src
import HomePage from '@/components/HomePage.vue'

export default {
  name: 'Home',
  components: {
    HomePage
  },
  data: function () {
  return {
    count: 0
  }
}
}
</script>
