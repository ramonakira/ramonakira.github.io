<template>
  <div>
    <div class="container mx-auto">
      <div class="text-3xl font-sans flex justify-between flex-col sm:flex-row">
        <h1 class="p-4 pt-8 pb-6 dark:border-b-zinc-300 dark:text-zinc-300 font-bold">
          Ramon de Jezus
        </h1>
        <div class="p-4 sm:pt-8 pb-6 flex w-28 justify-between">
          <a href="https://mastodon.social/@ramonakira" rel="me">
            <iconMastodon />
            <span class="sr-only">Mastodon</span>
          </a>

          <a href="https://github.com/ramonakira">
            <iconGithub />
            <span class="sr-only">Github</span>
          </a>

          <a href="https://www.linkedin.com/in/ramon-de-jezus-b7b66014/">
            <iconLinkedIn />
            <span class="sr-only">LinkedIn</span>
          </a>
        </div>
      </div>
      <div>
        <template v-for="(project, index) in projects">
          <div :key="index" class="m-4 mb-20 sm:mb-24 sm:grid sm:grid-cols-3 sm:gap-4">
            <div class="bg-slate-400 col-span-2 sm:max-w-[800px] aspect-[16/10]">
              <img
                class="border-2 border-gray-700"
                :src="project.image"
                :alt="project.image_alt"
                loading="lazy"
              >
            </div>
            <div class="">
              <h2 class="pt-4 pb-4">
                <template v-if="project.url">
                  <a :href="project.url" class="underline flex items-center hover:text-zinc-600 dark:text-zinc-300"><span>{{ project.title }}</span> <iconExternalLink /></a>
                </template>
                <template v-else>
                  <span class="line-through dark:text-zinc-300">{{ project.title }}</span>
                </template>
              </h2>
              <p class="dark:text-zinc-200" v-html="project.text" />
            </div>
          </div>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  head () {
    return {
      bodyAttrs: {
        class: 'dark:bg-zinc-900'
      }
    }
  },
  data () {
    return {
      projects: [
        {
          title: 'The geography of future water challenges',
          image: require('~/static/images/gfwc.jpg'),
          image_alt: 'Screenshot van The geography of future water challenges',
          url: 'https://themasites.pbl.nl/future-water-challenges/',
          text: 'Digitale versie van het gelijknamige boek. De site is gemaakt in Nuxt.js en wordt als een statische site gebouwd. Er wordt gebruik gemaakt van highcharts en highmaps om de grafieken en kaarten te genereren.'
        },
        {
          title: 'Vrijfijn',
          image: require('~/static/images/vrijfijn_nl.jpg'),
          image_alt: 'Screenshot van Vrijfijn.nl',
          url: 'https://www.vrijfijn.nl/',
          text: 'Webapplicatie met een zelftest en een intake voor de online behandelomgeving. De site is gemaakt met Django en jQuery.'
        },
        {
          title: '99gram',
          image: require('~/static/images/99gram_nl.jpg'),
          image_alt: 'Screenshot van 99gram.nl',
          url: 'https://www.99gram.nl/',
          text: 'Webapplicatie met een gecombineerde zelftest/intake die dient als voorportaal voor de behandelomgeving van Jouw Omgeving. De website bevat een forum en veel informatie toegespitst op de doelgroep. Achter de schermen draait de website op Wagtail in combinatie met jQuery en Vue.js voor de intake.'
        },
        {
          title: 'EU JAMRAI datavisualisatie',
          image: require('~/static/images/eu-jamrai.png'),
          image_alt: 'Screenshot van de datavisualisatie op de EU-JAMRAI website',
          url: 'https://eu-jamrai.eu/strengthening-national-response-country-to-country-visits/',
          text: 'Interactieve datavisualisatie om de <span class="italic">country-to-country</span> bezoeken van wetenschappers in kaart te brengen. De visualisatie is gemaakt in Nuxt.js en draait als een embed binnen de site.'
        },
        {
          title: 'NWO datavisualisatie',
          image: require('~/static/images/nwo_datavisualisatie.png'),
          image_alt: 'Screenshot van de NWO datavisualisatie',
          text: 'Interactieve datavisualisatie in de vorm van een Sankey-diagram die de geldstromen van het NWO weergeeft, als onderdeel van het jaarverslag. De visualisatie is gebouwd in Nuxt.js.'
        },
        {
          title: 'Urentracker',
          image: require('~/static/images/urentracker.png'),
          image_alt: 'Screenshot van een lege urentracker',
          text: 'Tool om het schrijven van uren te vereenvoudigen. De tool is geschreven in Nuxt.js en gebruikt de API van Teamwork om de data weer te geven en op te slaan.'
        }
      ]
    }
  }
}
</script>
