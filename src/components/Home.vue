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
    {{ homeText }}
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
      homeText: this.siteData.home.text,
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

<style>

</style>
