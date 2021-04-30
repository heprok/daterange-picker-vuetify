<template>
  <div id="app">
    <v-app>
      <v-content>
        <v-container>
          {{ range }}
          <DaterangePickerVuetify
            v-model="range"
            :display-format="displayFormat"
            no-title
            :input-props="inputProps"
            :menu-props="menuProps"
            :presets="presets"
          >
            <h3 slot="title">Vuetify Dater Range Picker - Next</h3>
          </DaterangePickerVuetify>
        </v-container>
      </v-content>
    </v-app>
  </div>
</template>

<script>
import Vue from 'vue';
import DaterangePickerVuetify from '@/daterange-picker-vuetify.vue';
import { format, subDays } from 'date-fns';
const displayFormat = 'yyyy-MM-dd';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    DaterangePickerVuetify
  },
    data() {
    return {
      range: {},
      displayFormat: displayFormat,
      inputProps: { solo: true, style: { width: '240px' } },
      menuProps: { offsetY: true, closeOnContentClick: false },
      presets: [
        {
          label: 'Today',
          range: [
            format(new Date(), 'yyyy-MM-dd'),
            format(new Date(), 'yyyy-MM-dd')
          ]
        },
        {
          label: 'Yesterday',
          range: [
            format(subDays(new Date(), 1), 'yyyy-MM-dd'),
            format(subDays(new Date(), 1), 'yyyy-MM-dd')
          ]
        },
        {
          label: 'Last 30 Days',
          range: [
            format(subDays(new Date(), 30), 'yyyy-MM-dd'),
            format(subDays(new Date(), 1), 'yyyy-MM-dd')
          ]
        }
      ]
    };
  }
});
</script>