<template>
  <div class="container mx-auto font-sans">
    <div class="flex justify-between flex-col sm:flex-row">
      <h1 class="text-3xl p-4 pt-8 pb-6 dark:border-b-zinc-300 dark:text-zinc-300 font-bold">
        Ramon de Jezus
      </h1>
      <div class="p-4 sm:pt-8 pb-6 flex justify-between">
        <a href="https://mastodon.social/@ramonakira" rel="me" class="pr-6">
          <iconMastodon />
          <span class="sr-only">Mastodon</span>
        </a>

        <a href="https://github.com/ramonakira" class="pr-6">
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
          <div>
            <h2 class="pb-4 text-lg font-semibold">
              <a
                v-if="project.url"
                :href="project.url"
                class="underline hover:text-zinc-600 dark:text-zinc-300"
              >
                <span>{{ project.title }}</span><iconExternalLink />
              </a>
              <span
                v-else
                class="line-through dark:text-zinc-300"
              >
                {{ project.title }}
              </span>
            </h2>
            <!-- eslint-disable-next-line vue/no-v-html -->
            <p class="dark:text-zinc-200" v-html="project.text" />
          </div>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
import { projects } from '~/assets/projects.js'

export default {
  data () {
    return {
      projects
    }
  },
  head () {
    return {
      bodyAttrs: {
        class: 'dark:bg-zinc-900'
      }
    }
  }
}
</script>
