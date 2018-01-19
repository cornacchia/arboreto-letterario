<template>
<div>
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
  <div class="col-xs-12" style="margin: 20px;">
    <h1 align="center">{{ title }}</h1>
    <h4 id="subtitle" align="center">{{ subtitle }}</h4>
    <span v-html="homeText"></span>
    <em>{{notes}}</em>
  </div>
</div>
</template>

<script>
import { QInput } from 'quasar'
import router from '../router'

export default {
  components: {
    QInput
  },
  data () {
    return {
      title: this.siteData.home.title,
      subtitle: this.siteData.home.subtitle,
      homeText: this.siteData.home.text,
      notes: this.siteData.home.notes,
      search: ''
    }
  },
  methods: {
    searchPlant () {
      let searchPlant = this.siteData.search[this.search]
      if (searchPlant) {
        router.replace({ path: 'plant', query: { name: searchPlant } })
      }
    }
  }
}
</script>

<style lang="stylus">
  #subtitle
    font-style italic
</style>
