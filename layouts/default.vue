<template>
  <v-app>
    <v-app-bar color="deep-purple" dark dense fixed clipped-left app>
      <v-btn text to="/">Nuxtify Learning</v-btn>
      <v-btn text to="/videos">Videos</v-btn>
    </v-app-bar>
    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>
  </v-app>
</template>
