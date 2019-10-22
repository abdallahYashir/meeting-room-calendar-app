<template>
  <v-container>
    <v-layout>
      <v-form v-model="current">
        <v-container>
          <v-row>
            <v-col cols="12" md="4">
              <v-text-field v-model="title" label="Title" solo></v-text-field>
            </v-col>
          </v-row>
        </v-container>
      </v-form>
    </v-layout>
    <v-sheet height="600">
      <v-calendar
      ref="calendar"
      type="week"
      color="primary"
      :value="today"
      :weekdays="weekdays"
      :events="events"
      >
      <!-- the events at the top (all-day) -->
      <template v-slot:day-header="{ date }">
        <template v-for="event in eventsMap[date]">
          <!-- all day events don't have time -->
          <div
          v-if="!event.time"
          :key="event.title"
          class="my-event"
          @click="open(event)"
          v-html="event.title"
          ></div>
        </template>
      </template>
      <!-- the events at the bottom (timed) -->
      <template v-slot:day-body="{ date, timeToY, minutesToPixels }">
        <template v-for="event in eventsMap[date]">
          <!-- timed events -->
          <div
          v-if="event.time"
          :key="event.title"
          :style="{ top: timeToY(event.time) + 'px', height: minutesToPixels(event.duration) + 'px' }"
          class="my-event with-time"
          @click="open(event)"
          v-html="event.title"
          ></div>
        </template>
      </template>
    </v-calendar>
  </v-sheet>
</v-container>
</template>

<script>
  import { DateTime } from 'luxon'
  const now = DateTime.local()

  export default {
    data: () => ({
      today: now.toLocaleString(),
      weekdays: [1, 2, 3, 4, 5],
      events: [
        {
          name: 'Weekly Meeting',
          start: '2019-10-22 09:00',
          end: '2019-10-22 10:00',
        },
      ],
    }),
    mounted () {
      this.$refs.calendar.scrollToTime('08:00')
    },
  };
</script>
