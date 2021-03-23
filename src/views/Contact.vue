<template>
  <div class="Contact">  
    <ContactPage/>
  </div>
</template>

<script>
// @ is an alias to /src
import ContactPage from '@/components/ContactPage.vue'

export default {
  name: 'Contact',
  components: {
    ContactPage
  },
  data: function () {
  return {
    count: 0
  }
}
}
</script>