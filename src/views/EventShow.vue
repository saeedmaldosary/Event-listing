<template>
  <div>
    <h1>{{ event.title }}</h1>
  </div>
</template>

<script>
import EventService from '@/services/EventService.js'
export default {
  props: ['id'],
  data() {
    return {
      event: {}
    }
  },
  created() {
    EventService.getEvent(this.id)
      .then((response) => {
        this.event = response.data // For now, logs out the response
        console.log(this.event)
      })
      .catch((error) => {
        console.log('There was an error:', error.response) // Logs out the error
      })
  }
}
</script>
