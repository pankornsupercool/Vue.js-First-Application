

<template>
  <div class="events">
    <h1>Event List</h1>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import EventService from "@/services/EventService.js"; //This is axios client file

export default {
  name: "Home",
  components: {
    EventCard,
  },
  data() {
    return {
      events: null,
    };
  },
  created() {
    EventService.getEvent().then(response => {
      this.events = response.data
    }).catch(error => {
      console.log(error)
    })
  },
};
</script>

<style scoped>
.events{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
