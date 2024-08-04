<template>
  <!---->
  <v-app>
    <v-app-bar app clipped-left v-if="isSmAndDown">
      <v-app-bar-nav-icon @click.stop="menu_sidebar = !menu_sidebar" />
      <v-toolbar-title>{{ title }}</v-toolbar-title>
    </v-app-bar>

    <v-navigation-drawer v-model="menu_sidebar" mobile-breakpoint="md">
      <v-container>
        <v-row>
          <v-col>
            <h1 v-if="!isSmAndDown">{{ title }}</h1>
            <h2>Navigation Drawer</h2>
          </v-col>
        </v-row>
      </v-container>
    </v-navigation-drawer>

    <v-main>
      <v-container fluid>
        <h1>MAIN</h1>
      </v-container>
    </v-main>

    <v-footer app>
      <span>My Footer</span>

      <v-btn @click="toggleTheme" variant="plain" size="x-small"
        >toggle theme</v-btn
      >
    </v-footer>
  </v-app>
</template>

<script setup>
import { ref } from "vue";
import { useDisplay, useTheme } from "vuetify";
const { mdAndUp, smAndDown } = useDisplay();
const isSmAndDown = ref(smAndDown);

const title = "The Title";

// menu_sidebar is true if we display in md
// md habe ich so festgelegt, siehe die Klasse des Menu-Buttons und den mobile-breakpoint des Navigation Drawers
// mdAndUp.value ist ein Boolean, der true ist, wenn die Bildschirmbreite >= 960px ist
const menu_sidebar = ref(mdAndUp);

const theme = useTheme();

const toggleTheme = () => {
  theme.global.name.value = theme.global.current.value.dark ? "light" : "dark";
};
</script>
