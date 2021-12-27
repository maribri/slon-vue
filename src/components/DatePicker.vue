<template>
  <v-menu
      ref="menu"
      v-model="menu"
      :close-on-content-click="false"
      :return-value.sync="dates"
      transition="scale-transition"
      offset-y
      :nudge-top="25"
      min-width="auto"
  >
    <template v-slot:activator="{ on, attrs }">
      <v-text-field
          v-model="dateRangeText"
          append-icon="mdi-calendar-blank-outline"
          readonly
          outlined
          dense
          v-bind="attrs"
          v-on="on"
          class="custom-textfield"
      ></v-text-field>
    </template>
    <v-date-picker
        v-model="dates"
        :first-day-of-week="1"
        max=2021-12-27
        no-title
        scrollable
        range
        class="custom-picker"
    >
      <v-spacer></v-spacer>
      <v-btn
          text
          color="primary"
          @click="menu = false"
      >
        Cancel
      </v-btn>
      <v-btn
          text
          color="primary"
          @click="$refs.menu.save(dates)"
      >
        OK
      </v-btn>
    </v-date-picker>
  </v-menu>
</template>

<script>
export default {
  data: () => ({
    dates: [/*'2021-12-07', '2021-12-21'*/],
    menu: false,
  }),
  computed: {
    dateRangeText() {
      return this.dates.map(d => this.formatDate(d)).join(" ~ ");
    },
  },
  methods: {
    formatDate(date) {
      if (!date) return null;
      const [year, month, day] = date.split("-");
      return `${day}-${month}-${year}`;
    },
  }
}
</script>
