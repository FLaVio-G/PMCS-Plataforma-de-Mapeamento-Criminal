<template>
  <v-app id="inspire">
    <v-app-bar
      app
      color="primary"
      flat
    >
      <v-container class="py-0 fill-height">
        <v-avatar
          class="mr-1"
          color="grey darken-1"
          size="38"
        ></v-avatar>

        <v-btn
          v-for="link in links"
          :key="link"
          text
        >
          {{ link }}
        </v-btn>
       

        <v-spacer></v-spacer>
 
        <v-responsive max-width="260">
          <v-text-field
            dense
            flat
            hide-details
            rounded
            solo-inverted
          ></v-text-field>
        </v-responsive>
      </v-container>
      
    </v-app-bar>

    <div class="home">
          <Mapa/>
      </div>
  </v-app>
  
</template>

<script>
import Mapa from "./components/Mapa"
export default {
  components: { Mapa },
  data: () => ({
    links: [
      "Seja um RND",
      "Sugestões",
      "Sobre",
      "Compartilhe a sua experiência",
    ],
  }),
};
</script>