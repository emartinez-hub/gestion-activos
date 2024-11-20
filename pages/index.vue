<template>
  <v-container fluid>
    <v-app-bar v-if="$vuetify.display.mdAndUp" :elevation="1">
      <v-toolbar-title>Dashboard</v-toolbar-title>
    </v-app-bar>

    <v-breadcrumbs class="pa-0">
      <v-breadcrumbs-item>
        <nuxt-link to="/">Home</nuxt-link>
      </v-breadcrumbs-item>
      <v-breadcrumbs-divider />
      <v-breadcrumbs-item disabled>Dashboard</v-breadcrumbs-item>
    </v-breadcrumbs>

    <v-row class="mt-3" dense>
      <v-col cols="12" md="6" lg="3">
        <v-card variant="tonal" :elevation="2" class="pa-3">
          <v-card-title class="d-flex align-center">
            <v-icon color="primary" class="me-3">mdi-cart</v-icon>
            Ventas | Hoy
          </v-card-title>
          <v-card-text>
            <h3 class="mb-2">RD$10,400.00</h3>
            <span class="text-success">0% Incremento</span>
          </v-card-text>
        </v-card>
      </v-col>

      <v-col cols="12" md="6" lg="3">
        <v-card variant="tonal" :elevation="2" class="pa-3">
          <v-card-title class="d-flex align-center">
            <v-icon color="orange" class="me-3">mdi-account-group</v-icon>
            Clientes | Hoy
          </v-card-title>
          <v-card-text>
            <h3 class="mb-2">5</h3>
            <span class="text-success">0% Incremento</span>
          </v-card-text>
        </v-card>
      </v-col>

      <v-col cols="12" md="6">
        <v-card variant="tonal" :elevation="2" class="pa-3">
          <v-card-title>Tráfico en PINA | Hoy</v-card-title>
          <v-card-text>
            <apex-chart
              type="donut"
              :options="chartOptions"
              :series="chartSeries"
              height="250"
            />
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts" setup>
import ApexChart from 'vue3-apexcharts';
import { reactive } from 'vue';

defineExpose({ ApexChart });

const chartSeries = [50, 30, 20];
const chartOptions = reactive({
  labels: ['Abiertos', 'Cerrados', 'Pendientes'],
  colors: ['#3366FF', '#00C49F', '#FFBB28'],
  legend: {
    position: 'bottom',
  },
  dataLabels: {
    enabled: true,
  },
});
</script>
