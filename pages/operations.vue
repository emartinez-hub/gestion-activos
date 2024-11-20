<template>
  <v-container fluid>
    <v-app-bar v-if="$vuetify.display.mdAndUp" :elevation="1">
      <v-toolbar-title>Operaciones</v-toolbar-title>
    </v-app-bar>

    <v-breadcrumbs class="pa-0">
        <v-breadcrumbs-item>
          <nuxt-link to="/">Home</nuxt-link>
        </v-breadcrumbs-item>
        <v-breadcrumbs-divider />
        <v-breadcrumbs-item disabled>Operaciones</v-breadcrumbs-item>
    </v-breadcrumbs>
  </v-container>
</template>
