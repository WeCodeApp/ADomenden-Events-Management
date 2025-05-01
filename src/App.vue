<template>
  <div class="container mt-5">
    <div class="bg-primary text-white py-4 rounded shadow-sm mb-4">
  <div class="container text-center">
    <h1 class="mb-0">
      <i class="bi bi-calendar-event me-2"></i>
      AR Domenden Event Management
    </h1>
  </div>
</div>


<div class="container">
<AddEvent :events="events" />
<EventList :events="events" />
</div>

    
  </div>
</template>

<script>
import AddEvent from './components/AddEvent.vue'
import EventList from './components/EventList.vue'
import eventsData from './components/data/events.json'

export default {
  components: {
    AddEvent,
    EventList
  },
  data() {
    return {
      events: eventsData.map(event => ({
        ...event,
        likes: 0 // Add default likes if missing
      }))
    }
  }
}
</script>
