<template>
  <q-layout>
    <q-toolbar slot="header" color="green">
      <q-btn flat @click="goHome">
        <q-icon name="home"
        />
      </q-btn>
      <q-toolbar-title>
        {{ title }}
      </q-toolbar-title>
    </q-toolbar>
    <q-input
    id="searchBar"
    placeholder="Cerca..."
    v-model="search"
    :after="[
      {
        icon: 'arrow_forward',
        content: true,
        handler: searchPlant
      }
    ]"
    />

    <div id="main" class="column scroll overflow-hidden">
      <router-view />
    </div>
  </q-layout>
</template>

<script>
import { QLayout, QToolbar, QToolbarTitle, QInput, QIcon, QBtn } from 'quasar'
import router from '../router'

export default {
  components: {
    QLayout,
    QToolbar,
    QToolbarTitle,
    QInput,
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
    searchPlant () {
      let searchPlant = this.siteData.search[this.search]
      if (searchPlant) {
        router.replace({ path: '/plant', query: { name: searchPlant } })
        return window.location.reload(true)
      }
    },
    goHome () {
      router.replace({path: '/home'})
    }
  }
}
</script>

<style lang="stylus">
  #searchBar
    margin 15px
</style>
