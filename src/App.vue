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
        <v-btn variant="text" @click="scrollTo(0)">Profile</v-btn>
        <v-divider vertical thickness="2px" length="8px" class="align-self-center"></v-divider>
        <v-btn variant="text" @click="scrollTo('.skills')">Skills</v-btn>
        <v-divider vertical thickness="2px" length="8px" class="align-self-center"></v-divider>
        <v-btn variant="text" @click="scrollTo('.portfolio')">Portfolio</v-btn>
      </v-container>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-card 
          color="transparent" 
          max-width="800px" 
          elevation="0"
          class="mt-16 profile">
          <v-card-item class="flex-grow">
            <template v-slot:prepend>
              <v-img src="/src/assets/pfp.png" height="200px" width="200px" rounded="50%"></v-img>
            </template>
            <v-card-item>
              <v-card-title class="text-headline-large">Hi! I'm Marvin de la Vega</v-card-title>
              <v-card-subtitle>A software engineer who loves to build ideas that solve real world problems</v-card-subtitle>
            </v-card-item>
            <v-card-item>
              <v-btn 
                variant="outlined" 
                color="primary" 
                prepend-icon="mdi-download" 
                href="../public/Marvin de la Vega - Resume v4.pdf"
                target="_blank"
                download>Download resume</v-btn>
              <v-btn 
                variant="outlined"
                prepend-icon="mdi-github" 
                href="https://github.com/marvin-delavega"
                target="_blank"
                download
                class="ml-2">
                Github
              </v-btn>
              <v-btn 
                variant="outlined" 
                color="yellow" 
                prepend-icon="mdi-coffee" 
                href="https://buymeacoffee.com/marvinducedelavega"
                target="_blank"
                download
                class="ml-2">Buy me coffee</v-btn>
            </v-card-item>
            <v-card-item>
              <v-btn 
                prepend-icon="mdi-phone"
                variant="text">+639945560115</v-btn>
              <v-btn 
                prepend-icon="mdi-facebook"
                href="https://www.facebook.com/marvin.delavega.10"
                target="_blank"
                variant="text">facebook</v-btn>
              <v-btn 
                prepend-icon="mdi-linkedin"
                href="https://www.linkedin.com/in/mducedv/"
                target="_blank"
                variant="text">linkedin</v-btn>
            </v-card-item>
          </v-card-item>
        </v-card>
        <v-divider class="mt-12"></v-divider>
        <v-card
          color="transparent" 
          max-width="1000px" 
          elevation="0"
          class="mt-16">
          <v-card-title class="text-title-medium text-center skills">
            Skills & Tech Stack
          </v-card-title>
          <v-container max-width="800px" class="mt-12">
            <v-row density="default" class="d-flex justify-center">
              <v-card v-for="skill in skills" color="transparent" elevation="0">
                <v-img :src="getSvgUrl(skill)" height="50"></v-img>
                <v-card-subtitle>{{ skill }}</v-card-subtitle>
              </v-card>
            </v-row>
          </v-container>
        </v-card>
        <v-card
          color="transparent" 
          max-width="1000px" 
          elevation="0"
          class="mt-16">
          <v-card-title class="text-title-medium text-center portfolio">
            Portfolio Projects
          </v-card-title>
          <v-container class="mt-12 d-flex flex-col ga-6 flex-wrap justify-center">
            <v-card 
              v-for="project in portfolio" 
              variant="tonal"
              width="290px"
              height="350px"
              class="d-flex flex-column">
              <v-card-item>
                <v-card-title class="text-title-large font-weight-semibold">{{ project.name }}</v-card-title>
                <v-card-subtitle>{{ project.kind }}</v-card-subtitle>
              </v-card-item>
              <v-card-subtitle>Role: {{ project.role }}</v-card-subtitle>
              <v-card-text class="flex-grow-1 text-grey-lighten-2">
                {{ project.desc }}
              </v-card-text>
              <v-card-item>
                <div class="d-flex justify-start align-center">
                  <v-img 
                    v-for="stack in project.stack" 
                    :key="stack"
                    :src="getSvgUrl(stack)" 
                    height="20" 
                    width="20"
                    class="stack-icon flex-grow-0 me-2"
                    v-tooltip="stack"
                  ></v-img>
                </div>
              </v-card-item>
              <v-divider class="flex-shrink-0 flex-grow-1"></v-divider>
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn 
                  :href="project.github" 
                  variant="outlined" 
                  target="_blank" 
                  prepend-icon="mdi-github"
                  :disabled="project.github == ''"
                  :text="(project.github == '' ? 'No' : '') + ' Source'">
                </v-btn>
                <v-btn 
                  v-if="project.liveURL !== ''" 
                  :href="project.liveURL" 
                  variant="outlined" 
                  target="_blank">
                    <template v-slot:prepend>
                      <v-img :src="getSvgUrl(project.liveHost)" width="16px"></v-img>
                    </template>
                    {{ project.liveHost }}
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-container>
        </v-card>
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts" setup>
import { onMounted, onUnmounted, ref } from 'vue';
import { useGoTo } from 'vuetify';

const isScrolled = ref(false)
const skills = ref<string[]>()

type Project = {
  name: string
  kind: string
  desc: string
  stack: string[]
  role: string
  github: string
  liveURL: string
  liveHost: string
}

const portfolio = ref<Project[]>()

const onScroll = () => {
  isScrolled.value = window.scrollY > 0
}

const goTo = useGoTo()
const scrollTo = (target: string | number) => {
  goTo(target, {duration: 300, easing: 'easeInOutCubic', offset: -128})
}

const svgModules = import.meta.glob('/src/assets/*.svg', { 
  query: '?url',
  import: 'default',
  eager: true,         
});

const getSvgUrl = (name: string) => {
  const path = `/src/assets/${name}.svg`;
  return svgModules[path] || '';
};

onMounted(() => {
  window.addEventListener('scroll', onScroll)

  skills.value = [
    'Csharp', 'Dot NET Core', 'Dot NET', 'TypeScript', 'Python',
    'FastAPI', 'JavaScript', 'Vue.js', 'Vite.js',
    'Vuetify', 'Tailwind CSS', 'MySQL', 'PostgresSQL',
    'Supabase', 'Redis', 'SQLite', 'Docker', 'Git'
  ]

  portfolio.value = [
    {
      name: 'SmartScraper',
      kind: 'Personal Project',
      desc: 'An autonomous job post web scraper using crawl4ai and ollama-hosted LLM to parse chunked markdown in a robust model call loop. It is then saved in supabase, and is viewable in a dashboard.',
      stack: ['Vue.js', 'Vite.js', 'Vuetify', 'TypeScript', 'Python', 'FastAPI', 'Supabase', 'Docker', 'Ollama'],
      github: 'https://github.com/marvin-delavega/smart-scraper',
      liveURL: 'https://smart-scraper-ashy.vercel.app/',
      liveHost: 'Vercel',
      role: 'Solo Fullstack'
    },
    {
      name: 'MsgMe',
      kind: 'Personal Project',
      desc: 'A simple stateless chat app that uses web sockets to recieve and maintain connections, and broadcast messages.',
      stack: ['Vue.js', 'Vite.js', 'Vuetify', 'TypeScript', 'Python', 'FastAPI', 'Docker'],
      github: 'https://github.com/marvin-delavega/msg-me',
      liveURL: 'https://msg-me-sepia.vercel.app/',
      liveHost: 'Vercel',
      role: 'Solo Fullstack'
    },
    {
      name: 'FraudDetection',
      kind: 'Personal Project',
      desc: 'A Card-Not-Present fraud detection pipeline with sync and async detection.',
      stack: ['Python', 'FastAPI', 'Supabase', 'Docker'],
      github: 'https://github.com/marvin-delavega/fraud-detection',
      liveURL: '',
      liveHost: '',
      role: 'Solo Backend'
    },
    {
      name: 'Operations Hub',
      kind: 'Commissioned Project | Agentic',
      desc: 'A warehousing and procurement network-local app that integrates to the client\'s existing ERP.',
      stack: ['TypeScript', 'Node.js', 'MySQL', 'Docker'],
      github: 'https://github.com/marvin-delavega/operations-hub',
      liveURL: '',
      liveHost: '',
      role: 'Solo Fullstack'
    },
    {
      name: 'Food & Beverage POS',
      kind: 'Work Project | Team',
      desc: 'A BIR accredited modern-look POS system with complete features you will need for a Food & Beverage business.',
      stack: ['Delphi', 'MySQL', 'Docker'],
      github: '',
      liveURL: 'https://activesystems.ph/',
      liveHost: 'Page',
      role: 'Team Lead & Backend'
    },
    {
      name: 'Work Management App',
      kind: 'Work Project | Team',
      desc: 'A complete HR and Payroll system',
      stack: ['Csharp', '.NET Core', 'PostgresSQL', 'Docker'],
      github: '',
      liveURL: 'https://activesystems.ph/',
      liveHost: 'Page',
      role: 'Team Lead & Backend'
    },
  ]
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
