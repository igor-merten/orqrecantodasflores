<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated color="primary">
      <q-toolbar>
        <q-toolbar-title>
          <img src="../statics/logo.png" style="width: 20%" class="q-mt-sm" />
          <!-- LOGO DO SITE BRANCA -->
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="rightDrawerOpen"
      side="right"
      show-if-above
      bordered
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Menu
        </q-item-label>
        <Menu
          v-for="link in opcoesMenu"
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
import Menu from 'components/Menu'
import { colors } from 'quasar'

const { lighten, setBrand } = colors

const newPrimaryColor = '#064319'
setBrand('primary', newPrimaryColor)
setBrand('primary-darkened', lighten(newPrimaryColor, -10))

export default {
  name: 'MainLayout',

  components: {
    Menu
  },

  data () {
    return {
      rightDrawerOpen: false,
      opcoesMenu: [
        {
          title: 'Adicionar Notificação',
          icon: 'add_alert',
          link: '#'
        }
        // {
        //   title: 'Github',
        //   caption: 'github.com/quasarframework',
        //   icon: 'code',
        //   link: 'https://github.com/quasarframework'
        // },
        // {
        //   title: 'Discord Chat Channel',
        //   caption: 'chat.quasar.dev',
        //   icon: 'chat',
        //   link: 'https://chat.quasar.dev'
        // },
        // {
        //   title: 'Forum',
        //   caption: 'forum.quasar.dev',
        //   icon: 'record_voice_over',
        //   link: 'https://forum.quasar.dev'
        // },
        // {
        //   title: 'Twitter',
        //   caption: '@quasarframework',
        //   icon: 'rss_feed',
        //   link: 'https://twitter.quasar.dev'
        // },
        // {
        //   title: 'Facebook',
        //   caption: '@QuasarFramework',
        //   icon: 'public',
        //   link: 'https://facebook.quasar.dev'
        // },
        // {
        //   title: 'Quasar Awesome',
        //   caption: 'Community Quasar projects',
        //   icon: 'favorite',
        //   link: 'https://awesome.quasar.dev'
        // }
      ]
    }
  }
}
</script>

<style>
</style>
