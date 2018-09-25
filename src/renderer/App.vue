<template>
  <div id="app">
    <v-app>
      <v-card>
        <v-tabs v-model="active" color="cyan" dark slider-color="yellow" show-arrows app>
          <v-tab v-for="tab in tabs" :key="tab.id" ripple>
            {{ tab.title }}
          </v-tab>
          <v-tabs-items>
            <v-tab-item v-for="(tab, i) of tabs" :id="tab.id" :key="tab.id">
              <webview :src="tab.src"></webview>
            </v-tab-item>
          </v-tabs-items>
        </v-tabs>
        <v-btn absolute dark fab bottom right icon color="pink" @click="newTab">
          <v-icon>add</v-icon>
        </v-btn>
      </v-card>
    </v-app>
  </div>
</template>

<script>
import { v4 } from 'uuid';

export default {
  name: "pbrowser",
  data: () => ({
    active: null,
    tabs: []
  }),
  methods: {
    newTab() {
      this.tabs.push({
        id: v4(),
        src: 'https://google.com',
      });
    }
  }
};
</script>

<style>
/* CSS */
</style>
