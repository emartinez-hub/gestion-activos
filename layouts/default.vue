<template>
  <v-layout>
    <v-app-bar>
      <v-app-bar-nav-icon
        variant="text"
        @click.stop="drawer = !drawer"
      ></v-app-bar-nav-icon>

      <v-toolbar-title>Gestión de Activos</v-toolbar-title>

      <v-spacer></v-spacer>

      <template v-if="$vuetify.display.mdAndUp">
        <v-btn icon="mdi-magnify" variant="text"></v-btn>
        <v-btn icon="mdi-filter" variant="text"></v-btn>
      </template>

      <v-btn icon="mdi-dots-vertical" variant="text"></v-btn>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      :location="$vuetify.display.mobile ? 'bottom' : undefined"
      temporary
      class="push"
    >
      <v-list :items="items"></v-list>
    </v-navigation-drawer>

    <v-main :class="{ 'shifted-main': drawer }" class="d-flex justify-center mt-15 pt-15 px-3" style="height: 500px">
      <slot />
    </v-main>
  </v-layout>
</template>

<script lang="ts" setup>
import { ref, watch } from 'vue';

const drawer = ref(true);
const group = ref(null);
const items = ref([
  { title: 'Foo', value: 'foo' },
  { title: 'Bar', value: 'bar' },
  { title: 'Fizz', value: 'fizz' },
  { title: 'Buzz', value: 'buzz' },
]);

watch(group, () => {
  drawer.value = false;
});
</script>

<style scoped>
.push {
  position: fixed;
  top: 0;
  left: 0;
  height: 100vh;
  width: 240px;
  transition: transform 0.3s ease;
}

.shifted-main {
  margin-left: 240px;
  transition: margin-left 0.3s ease;
}
</style>
