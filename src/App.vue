<template>
  <v-app id="scroll-target" class="dark-gradient">
    <v-app-bar 
      color="transparent"
      elevation="0"
      density="prominent"
      scroll-behavior="elevated"
      scroll-threshold="50" 
      :class="isScrolled ? 'dark-gradient' : ''">
      <v-container class="d-flex justify-center align-center" height="100%">
        <v-btn variant="text">Profile</v-btn>
        <v-divider vertical thickness="2px" length="8px" class="align-self-center"></v-divider>
        <v-btn variant="text">Skills</v-btn>
        <v-divider vertical thickness="2px" length="8px" class="align-self-center"></v-divider>
        <v-btn variant="text">Portfolio</v-btn>
        <v-divider vertical thickness="2px" length="8px" class="align-self-center"></v-divider>
        <v-btn variant="text">Contacts</v-btn>
      </v-container>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-card 
          color="transparent" 
          max-width="800px" 
          elevation="0"
          class="mt-16">
          <v-card-item class="flex-grow">
            <template v-slot:prepend>
              <v-img src="/src/assets/pfp.png" height="200px" width="200px" rounded="50%"></v-img>
            </template>
            <v-card-item>
              <v-card-title class="text-headline-large">Hi! I'm Marvin de la Vega</v-card-title>
              <v-card-subtitle>A software engineer who loves to build ideas that solve real world problems</v-card-subtitle>
              <v-btn 
                variant="outlined" 
                color="primary" 
                append-icon="mdi-download" 
                class="mt-6">Download resume</v-btn>
            </v-card-item>
          </v-card-item>
        </v-card>
        <v-divider class="mt-12"></v-divider>
        <v-card
          color="transparent" 
          max-width="1000px" 
          elevation="0"
          class="mt-16">
          <v-card-title class="text-title-medium text-center">
            Skills & Tech Stack
          </v-card-title>
          <v-container max-width="800px" class="mt-12">
            <v-row density="compact">
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Csharp.svg" height="50"></v-img>
                <v-card-subtitle>C#</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/NET core.svg" height="50"></v-img>
                <v-card-subtitle>.NET Core</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/NET.svg" height="50"></v-img>
                <v-card-subtitle>.NET</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/TypeScript.svg" height="50"></v-img>
                <v-card-subtitle>TypeScript</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Python.svg" height="50"></v-img>
                <v-card-subtitle>Python</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/FastAPI.svg" height="50"></v-img>
                <v-card-subtitle>FastAPI</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Java.svg" height="50"></v-img>
                <v-card-subtitle>Java</v-card-subtitle>
              </v-card>
            </v-row>
            <v-row density="compact" class="mt-8">
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/JavaScript.svg" height="50"></v-img>
                <v-card-subtitle>JavaScript</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Vue.js.svg" height="50"></v-img>
                <v-card-subtitle>Vue.js</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Vite.js.svg" height="50"></v-img>
                <v-card-subtitle>Vite.js</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Vuetify.svg" height="50"></v-img>
                <v-card-subtitle>Vuetify</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Tailwind CSS.svg" height="50"></v-img>
                <v-card-subtitle>Tailwind CSS</v-card-subtitle>
              </v-card>
            </v-row>
            <v-row density="compact" class="mt-8">
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/MySQL.svg" height="50"></v-img>
                <v-card-subtitle>MySQL</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/PostgresSQL.svg" height="50"></v-img>
                <v-card-subtitle>PostgreSQL</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Supabase.svg" height="50"></v-img>
                <v-card-subtitle>Supabase</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Redis.svg" height="50"></v-img>
                <v-card-subtitle>Redis</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/SQLite.svg" height="50"></v-img>
                <v-card-subtitle>SQLite</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Docker.svg" height="50"></v-img>
                <v-card-subtitle>Docker</v-card-subtitle>
              </v-card>
              <v-card color="transparent" elevation="0"> 
                <v-img src="/src/assets/Git.svg" height="50"></v-img>
                <v-card-subtitle>Git</v-card-subtitle>
              </v-card>
            </v-row>
          </v-container>
        </v-card>
        <v-card
          color="transparent" 
          max-width="1000px" 
          elevation="0"
          class="mt-16">
          <v-card-title class="text-title-medium text-center">
            Portfolio
          </v-card-title>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts" setup>
import { onMounted, onUnmounted, ref } from 'vue';


const isScrolled = ref(false)

const onScroll = () => {
  isScrolled.value = window.scrollY > 0
}

onMounted(() => {
  window.addEventListener('scroll', onScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
})

</script>

<style>
.dark-gradient {
  background: linear-gradient(135deg, #0f172a 0%, #020617 100%);
}
</style>
