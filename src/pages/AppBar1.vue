<template>
  <v-app>
    <v-app-bar v-if="isXs" app>
      <v-app-bar-title>My App</v-app-bar-title>
    </v-app-bar>

    <v-main>
      <v-container>
        <h1>Welcome to My App</h1>
        <!-- Der Rest des Inhalts -->
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from "vue";
import { useDisplay } from "vuetify";

const { xs } = useDisplay();
const isXs = ref(xs);
</script>
