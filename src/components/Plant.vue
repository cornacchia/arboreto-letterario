<template>
  <div>
    <img :src="picturePath" style="max-height: 500px; width: 100%;" />

    <q-list
     striped
     style="margin: 20px;">
      <q-collapsible
      v-for="(source, index) of sources"
      :key="index"
      :label="source.title"
      :sublabel="source.subtitle">
        {{source.text}}
      </q-collapsible>
    </q-list>
  </div>
</template>

<script>
import { QList, QCollapsible } from 'quasar'

export default {
  components: {
    QList,
    QCollapsible
  },
  data () {
    const name = this.$route.query.name

    return {
      picturePath: this.siteData.plants[name].picture,
      sources: this.siteData.plants[name].sources
    }
  }
}
</script>

<style>

</style>
