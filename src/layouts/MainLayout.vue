<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Qualificacions App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label header>
          <p>{{ date }}</p>
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Login',
    caption: 'Iniciar Sesion.',
    icon: 'login',
    link: 'http://localhost:8080/#/Login'
  },
  {
    title: 'About',
    caption: 'Información.',
    icon: 'info',
    link: 'http://localhost:8080/#/About'
  }
  /*  {
    title: '',
    caption: '',
    icon: '',
    link: 'http://localhost:8080/#/awdaw'
  },
  {
    title: 'errorTest',
    caption: 'error_page.',
    icon: 'error',
    link: 'http://localhost:8080/#/awdaw'
  } */
]

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: { EssentialLink },

  computed: {
    date () {
      const date = new Date()
      const format = {
        weekday: 'long',
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      }
      return date.toLocaleDateString('es-ES', format)
    }
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
