<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>
<script>
import EventServices from '@/services/EventServices.js'
export default {
  name: 'EventDetails',
  props: ['id'],
  data() {
    return {
      event: null,
    }
  },
  created() {
    EventServices.getEvent(this.id)
      .then((resp) => (this.event = resp.data))
      .catch((error) => console.log(error))
  },
}
</script>
