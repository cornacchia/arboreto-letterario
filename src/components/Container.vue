<template>
  <q-layout>
    <q-toolbar slot="header" color="green">
      <q-btn flat @click="goHome">
        <q-icon name="home" />
      </q-btn>
      <q-toolbar-title>
        {{ title }}
      </q-toolbar-title>
    </q-toolbar>
    <div id="main" class="column scroll overflow-hidden">
      <router-view />
    </div>
  </q-layout>
</template>

<script>
import { QLayout, QToolbar, QToolbarTitle, QIcon, QBtn } from 'quasar'
import router from '../router'

export default {
  components: {
    QLayout,
    QToolbar,
    QToolbarTitle,
    QIcon,
    QBtn
  },
  data () {
    return {
      title: this.siteData.title,
      search: ''
    }
  },
  methods: {
    goHome () {
      router.replace({ path: 'home' })
    }
  }
}
</script>

<style lang="stylus">
  #searchBar
    margin 15px
</style>
