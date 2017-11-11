<template>
  <q-layout>
    <q-toolbar slot="header" color="green">
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
import { QLayout, QToolbar, QToolbarTitle } from 'quasar'

export default {
  components: {
    QLayout,
    QToolbar,
    QToolbarTitle
  },
  data () {
    return {
      title: this.siteData.title
    }
  }
}
</script>

<style>

</style>
