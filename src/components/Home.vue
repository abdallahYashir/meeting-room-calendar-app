<template>
  <v-container>
    <v-subheader :inset="true">Book meeting room</v-subheader>
    <v-sheet height="600">
      <v-calendar
      ref="calendar"
      type="week"
      color="primary"
      :value="today"
      :weekdays="weekdays"
      :events="events"
      ></v-calendar>
    </v-sheet>
  </v-container>
</template>

<script>
  import { DateTime } from 'luxon'

  export default {
    data: () => ({
      today: DateTime.local().toLocaleString(),
      weekdays: [1, 2, 3, 4, 5],
      events: [
      {
        name: 'Meeting',
        start: '2019-01-07',
        end: '2019-01-07'
      },
      ],
    }),
    mounted () {
      this.$refs.calendar.scrollToTime('08:00')
    },
  };
</script>
