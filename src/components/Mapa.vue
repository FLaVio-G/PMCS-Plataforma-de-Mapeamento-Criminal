<template>
  <v-main>
    <v-container>
      <v-row>
        <v-col cols="2">
          <v-sheet rounded="lg">
            <v-card class="mx-auto" max-width="500">
              <v-list>
                <v-list-item-group v-model="model">
                  <v-list-item v-for="(item, i) in items" :key="i">
                    <v-list-item-icon>
                      <v-icon v-text="item.icon"></v-icon>
                    </v-list-item-icon>
                    <v-list-item-content>
                      <v-list-item-title v-text="item.text"></v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                </v-list-item-group>
              </v-list>
            </v-card>
          </v-sheet>
        </v-col>

        <v-col>
          <v-sheet min-height="70vh" rounded="lg">
            id = map
       
         </v-sheet>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<style>
 #map {
    height: 50%;
  }
</style>

<script>
export default {
   data: () => ({
      items: [
        {
          icon: 'mdi-inbox',
          text: 'Gravíssimos',
        },
        {
          icon: 'mdi-star',
          text: 'Grave',
        },
        {
          icon: 'mdi-send',
          text: 'Mediano',
        },
        {
          icon: 'mdi-email-open',
          text: 'Alertas',
        },
      ],
      model: 1,
    }),
   }
</script>
