<template>
  <div class="q-px-lg q-py-md">
    <q-timeline :layout="layout" color="secondary">

      <template v-for="(event, index) in timelineData" :key="index">
        <q-timeline-entry v-if="event.heading===1" heading>
          <div>{{ event.title }}</div>
          <br>
          <!-- ({{$q.screen.lt.sm ? 'Dense' : ($q.screen.lt.md ? 'Comfortable' : 'Loose')}} layout) -->
        </q-timeline-entry>
        <q-timeline-entry
          v-if="event.heading===0"
          :title="event.title"
          :subtitle="event.subtitle"
          :side="event.side"
          :icon="event.icon"
          :color="event.color"
        >
          <div>{{ event.description }}</div>
        </q-timeline-entry>
      </template>
    </q-timeline>
  </div>
</template>

<script setup lang="ts">
import { useQuasar } from 'quasar'
import { computed } from 'vue'

const $q = useQuasar()

const layout = computed(() => {
  return $q.screen.lt.sm ? 'dense' : ($q.screen.lt.md ? 'comfortable' : 'loose')
})

const timelineData = [
  {
    title: "Year 2018",
    subtitle: "February 22, 2022",
    side: "left",
    icon: null,
    color: null,
    heading:1,
    description: ""
  },
  {
    title: "Event Title",
    subtitle: "February 22, 1986",
    side: "left",
    icon: null,
    color: null,
    heading:0,
    description: "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
  },
  {
    title: "Event Title",
    subtitle: "February 22, 2022",
    side: "left",
    icon: null,
    color: null,
    heading:0,
    description: "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."
  },
  // Add more timeline events here
];
</script>
