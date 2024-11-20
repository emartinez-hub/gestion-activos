<template>
  <v-card>
    <v-layout>
      <v-app-bar prominent>
        <v-app-bar-nav-icon
          variant="text"
          @click.stop="drawer = !drawer"
        ></v-app-bar-nav-icon>

        <v-toolbar-title>Gestión de Activos</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn @click="toggleTheme" icon="mdi-theme-light-dark" variant="text"></v-btn>
      </v-app-bar>

      <v-navigation-drawer
        v-model="drawer"
        :temporary="$vuetify.display.mobile"
      >
        <v-divider></v-divider>

        <v-list density="compact" nav>
          <nuxt-link to="/">
            <v-list-item
              prepend-icon="mdi-view-dashboard"
              title="Dashboard"
              value="dashboard"
            />
          </nuxt-link>

          <nuxt-link to="/operations">
            <v-list-item
              prepend-icon="mdi-cog-transfer"
              title="Operaciones"
              value="operations"
            />
          </nuxt-link>

          <nuxt-link to="/shipping">
            <v-list-item
              prepend-icon="mdi-package-variant"
              title="Shipping"
              value="shipping"
            />
          </nuxt-link>

          <nuxt-link to="/customer-service">
            <v-list-item
              prepend-icon="mdi-headset"
              title="Servicio al cliente"
              value="customer-service"
            />
          </nuxt-link>

          <nuxt-link to="/finances">
            <v-list-item
              prepend-icon="mdi-currency-usd"
              title="Finanzas"
              value="finances"
            />
          </nuxt-link>

          <nuxt-link to="/settings">
            <v-list-item
              prepend-icon="mdi-cog-outline"
              title="Configuraciones"
              value="settings"
            />
          </nuxt-link>

          <nuxt-link to="/reports">
            <v-list-item
              prepend-icon="mdi-file-chart"
              title="Reportes"
              value="reports"
            />
          </nuxt-link>

          <nuxt-link to="/my-tickets">
            <v-list-item
              prepend-icon="mdi-ticket-account"
              title="Mis tickets"
              value="my-tickets"
            />
          </nuxt-link>
        </v-list>
      </v-navigation-drawer>

      <v-main>
        <slot />
      </v-main>
    </v-layout>
  </v-card>
</template>

<script lang="ts" setup>
import { ref } from 'vue';
import { useTheme } from 'vuetify';

const drawer = ref(true);
const theme = useTheme();

function toggleTheme() {
  theme.global.name.value = theme.global.current.value.dark ? 'light' : 'dark';
}
</script>
