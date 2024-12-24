<template>
  <v-app >
    <v-app-bar  
      color="primary"
      dark
      
      >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Aprendiendo.com</v-toolbar-title>

      <v-spacer></v-spacer>
      <router-link to='/'>
        <v-btn text>
          <span class="mr-2">Home </span>
        </v-btn>
      </router-link> |
        
      <router-link to='/administracion'>
        <v-btn text>
        <span class="mr-2"> Administracion </span>
        </v-btn>
      </router-link> 
      
      
    </v-app-bar>
    

    <v-main class="blue lighten-3">
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
