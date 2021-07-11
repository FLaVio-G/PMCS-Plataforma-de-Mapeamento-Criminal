<template>
  <v-app id="inspire">
    <v-app-bar app color="primary" flat>
      <v-container class="py-0 fill-height">
        <v-avatar class="mr-10" color="grey darken-1" size="38"></v-avatar>

        <v-btn to = "/" text>
         Mapa
        </v-btn>

        <v-btn href=https://www.instagram.com/mapeamentocriminalsantareno/ text>
         Compartilhe sua Experiência
        </v-btn>

         <v-btn to = "/sobre" text>
        Sobre
        </v-btn>

        <v-spacer></v-spacer>
      </v-container>
    </v-app-bar>
<router-view/>

  </v-app>
</template>

<script>
import Mapa from "./components/Mapa";
export default {
  components: { Mapa },
};
</script>