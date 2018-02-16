<template>
<div>
  <q-carousel arrows dots autoplay infinite style="width: 100%;">
    <div slot="slide"
      v-for="(picture, index) of carouselPictures"
      :key="index"
      class="centered">
        <img class="picture" :src="picture.path" />
    </div>
  </q-carousel>
  <div class="col-xs-12" style="margin: 20px;">
    <h1 align="center">{{ title }}</h1>
    <h4 id="subtitle" align="center">{{ subtitle }}</h4>
    <span v-html="homeText"></span>
    <em>{{notes}}</em>
  </div>
</div>
</template>

<script>
import { QCarousel } from 'quasar'
import router from '../router'
import siteData from '../data'

export default {
  components: {
    QCarousel
  },
  data () {
    return {
      carouselPictures: siteData.home.carouselPictures,
      title: siteData.home.title,
      subtitle: siteData.home.subtitle,
      homeText: siteData.home.text,
      notes: siteData.home.notes,
      search: ''
    }
  },
  methods: {
    searchPlant () {
      let searchPlant = siteData.search[this.search]
      if (searchPlant) {
        router.push({ path: '/plant/' + searchPlant })
      }
    }
  }
}
</script>

<style lang="stylus">
  #subtitle
    font-style italic
  .picture
    width 100%
</style>
