<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <v-card 
      elevated="3"
      max-width="1200"
      class="mx-auto"
      >
      <v-layout>
          <v-app-bar 
           color="#FB8C00">

            <template v-slot:prepend>
              <v-btn
                :to="{name: 'home'}"
              >
                SoftOil | CONAGUA
              </v-btn>
            </template>
            
            <template v-slot:append>
              <v-btn :to="{name: 'home'}">
                inicio
              </v-btn>
              <v-btn :to="{name: 'login'}">
                ingresar
              </v-btn>
            </template>

          </v-app-bar>

        <v-main>
          <v-container>
            <RouterView />
          </v-container>
        </v-main>  
      </v-layout>
  </v-card>
</template>
