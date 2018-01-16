<template>
  <div>

    <q-carousel arrows dots autoplay infinite style="width: 100%;">
      <div slot="slide"
        id="slides"
        v-for="(picture, index) of carouselPictures"
        :key="index"
        class="bg-tertiary centered">
          <img :src="picture.path" style="width: 100%; max-height: 500px;" />
      </div>
    </q-carousel>

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
import { QList, QCollapsible, QCarousel } from 'quasar'

export default {
  components: {
    QList,
    QCollapsible,
    QCarousel
  },
  data () {
    const name = this.$route.query.name
    return {
      carouselPictures: this.siteData.plants[name].carouselPictures,
      sources: this.siteData.plants[name].sources
    }
  }
}
</script>

<style lang="stylus">
</style>
