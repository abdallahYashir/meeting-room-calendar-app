<template>
  <v-container>
    <v-subheader :inset="true">Book meeting room</v-subheader>
    <v-sheet height="500">
      <v-calendar
      type="week"
      now="2019-01-08"
      value="2019-01-08"
      :weekdays="weekdays"
      :events="events"
      ></v-calendar>
    </v-sheet>
  </v-container>
</template>

<script>
  export default {
    data: () => ({
      weekdays: [1, 2, 3, 4, 5],
      events: [
      {
        name: 'Vacation',
        start: '2018-12-30',
        end: '2019-01-02',
      },
      {
        name: 'Meeting',
        start: '2019-01-07',
      },
      {
        name: '30th Birthday',
        start: '2019-01-03',
      },
      {
        name: 'New Year',
        start: '2019-01-01',
      },
      {
        name: 'Conference',
        start: '2019-01-21',
      },
      {
        name: 'Hackathon',
        start: '2019-01-30',
        end: '2019-02-01',
      },
      ],
    }),
  };
</script>
