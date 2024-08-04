<template>
  <!---->

  <v-app-bar app clipped-left>
    <v-app-bar-nav-icon
      @click.stop="menu_sidebar = !menu_sidebar"
      class="d-md-none"
    />
    <v-toolbar-title>Nav Layout 1</v-toolbar-title>
    <v-spacer />
    <v-btn icon>
      <v-icon>mdi-magnify</v-icon>
    </v-btn>
    <v-btn icon>
      <v-icon>mdi-heart</v-icon>
    </v-btn>
    <v-btn icon>
      <v-icon>mdi-dots-vertical</v-icon>
    </v-btn>

    <v-spacer />

    <v-menu :close-on-content-click="false">
      <template v-slot:activator="{ props }">
        <v-btn icon v-bind="props">
          <v-icon>mdi-account-circle</v-icon>
        </v-btn>
      </template>

      <v-sheet rounded="lg" elevation="6">
        <v-list>
          <v-list-item>
            <v-list-item-title>Profile</v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>Settings</v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>Logout</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-sheet>
    </v-menu>
  </v-app-bar>

  <AppFooter />

  <!---->

  <v-navigation-drawer v-model="menu_sidebar" mobile-breakpoint="md">
    <!-- v-model="customizer.Sidebar_drawer"
    :rail="customizer.mini_sidebar" -->

    <v-container>
      <v-row>
        <v-col>
          <h1>Navigation Drawer</h1>
        </v-col>
      </v-row>
    </v-container>
  </v-navigation-drawer>

  <!---->

  <v-main>
    <v-container fluid>
      <h1>MAIN</h1>
    </v-container>
  </v-main>
</template>

<script setup>
import { onMounted, ref } from "vue";
import { useDisplay } from "vuetify";
const { mdAndUp } = useDisplay();

// menu_sidebar is true if we display in md
// md habe ich so festgelegt, siehe die Klasse des Menu-Buttons und den mobile-breakpoint des Navigation Drawers
// mdAndUp.value ist ein Boolean, der true ist, wenn die Bildschirmbreite >= 960px ist
let menu_sidebar = ref(null);

onMounted(() => {
  menu_sidebar.value = mdAndUp.value;
});
</script>
