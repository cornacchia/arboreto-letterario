<template>
  <q-layout v-model="sides">
    <q-toolbar slot="header" color="green">
      <q-btn flat @click="goHome">
        <q-icon name="home" />
      </q-btn>
      <q-toolbar-title>
        {{ title }}
      </q-toolbar-title>
      <q-btn flat @click="sides.right = !sides.right">
        <q-icon name="menu" />
      </q-btn>
    </q-toolbar>
    <div slot="right">
      <q-list no-border link inset-separator>
        <q-list-header>Piante</q-list-header>
        <q-item @click="navigateUlivo">
          <q-item-side icon="ion-leaf" />
          <q-item-main label="Ulivo" />
        </q-item>
        <q-item @click="navigateQuercia">
          <q-item-side icon="ion-leaf" />
          <q-item-main label="Quercia" />
        </q-item>
        <q-item @click="navigateVite">
          <q-item-side icon="ion-leaf" />
          <q-item-main label="Vite" />
        </q-item>
      </q-list>
    </div>
    <div id="main" class="column scroll overflow-hidden">
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
      <router-view />
    </div>
  </q-layout>
</template>

<script>
import { QLayout, QToolbar, QToolbarTitle, QIcon, QBtn, QInput,
  QList, QListHeader, QSideLink, QItem, QItemSide, QItemMain } from 'quasar'
import siteData from '../data'

export default {
  components: {
    QLayout,
    QToolbar,
    QToolbarTitle,
    QIcon,
    QBtn,
    QInput,
    QListHeader,
    QList,
    QItem,
    QSideLink,
    QItemSide,
    QItemMain
  },
  data () {
    return {
      title: siteData.title,
      search: '',
      sides: {
        right: false,
        left: false
      }
    }
  },
  methods: {
    goHome () {
      window.location = '/home'
    },
    searchPlant () {
      let searchPlant = siteData.search[this.search]
      if (searchPlant) {
        window.location = '/plant/' + searchPlant
      }
    },
    navigateUlivo () {
      window.location = '/plant/ulivo'
    },
    navigateQuercia () {
      window.location = '/plant/quercia'
    },
    navigateVite () {
      window.location = '/plant/vite'
    }
  }
}
</script>

<style lang="stylus">
  #searchBar
    margin 15px
</style>
