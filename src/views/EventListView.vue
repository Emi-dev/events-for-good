<script setup>
import { ref, onMounted } from "vue";
import EventService from "@/services/EventService.js";
import EventCard from "../components/EventCard.vue";

/* 
  Mock Database:
  https://github.com/Code-Pop/Real-World-Vue-3-New-Syntax/blob/main/db.json
  http://my-json-server.typicode.com/Code-Pop/Real-World_Vue-3/events
*/

const events = ref(null);

onMounted(() => {
  EventService.getEvents()
    .then((response) => {
      events.value = response.data;
    })
    .catch((error) => {
      console.log(error);
    });
});
</script>

<template>
  <h1>Events For Good</h1>
  <div class="events">
    <!-- 
      v-bind: Dynamically bind one or more attributes, or a component prop to an expression.
      ":" is shorthand for "v-bind" (v-bind:event = :event) 
    -->
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
