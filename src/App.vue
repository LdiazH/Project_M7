<template>
  <v-app>
    <v-app-bar
      
      color="primary"
      dark
      
      
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Aprendiendo.com</v-toolbar-title>

      <v-spacer></v-spacer>
      <router-link to="/">Home </router-link>  |
      <router-link to="/administracion">Administracion</router-link>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>
    

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
