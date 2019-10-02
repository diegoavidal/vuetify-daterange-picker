<template>
  <div id="app">
    <v-app>
      <v-content>
        <v-container>
          {{ range }}
          <v-daterange
            v-model="range"
            :display-format="displayFormat"
            no-title
            :input-props="inputProps"
            :menu-props="menuProps"
            :presets="presets"
          >
            <h3 slot="title">Vuetify Dater Range Picker - Next</h3>
          </v-daterange>
        </v-container>
      </v-content>
    </v-app>
  </div>
</template>
<script>
import VDaterange from '@/components/VDaterange';
import { format, subDays } from 'date-fns';

const displayFormat = 'yyyy-MM-dd';

export default {
  name: 'app',
  components: { VDaterange },
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
};
</script>
