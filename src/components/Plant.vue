<template>
  <div>
    <h2 align="center">{{title}}</h2>
    <q-carousel arrows dots autoplay infinite style="width: 100%;">
      <div slot="slide"
        v-for="(picture, index) of carouselPictures"
        :key="index"
        class="centered">
          <img class="picture" :src="picture.path" />
      </div>
    </q-carousel>

    <q-list
     separator
     no-border
     style="margin: 20px;">
      <q-list-header>Fonti</q-list-header>
      <q-collapsible
      v-for="(source, index) of sources"
      :key="index"
      :label="source.title"
      :sublabel="source.subtitle">
      <div id="buttonRow" class="row">
        <q-btn class="rowButton" color="primary" style="margin-right: 5px;">
          <q-icon name="picture_as_pdf" /> Scarica PDF
        </q-btn>
        <q-btn class="rowButton" color="primary">
          <q-icon name="audiotrack" /> Ascolta audio
        </q-btn>
        </div>
        <div class="row">
        <span class="sourceText" v-html="source.text"></span>
        </div>
      </q-collapsible>
    </q-list>

  </div>
</template>

<script>
import { QList, QListHeader, QCollapsible, QCarousel, QBtn, QIcon } from 'quasar'
import siteData from '../data'

export default {
  components: {
    QList,
    QListHeader,
    QCollapsible,
    QCarousel,
    QBtn,
    QIcon
  },
  props: ['name'],
  data () {
    const name = this.$route.params.name
    return {
      carouselPictures: siteData.plants[name].carouselPictures,
      sources: siteData.plants[name].sources,
      title: siteData.plants[name].title
    }
  }
}
</script>

<style lang="stylus">
  #buttonRow
    align center
    margin-bottom 10px
  .rowButton
    margin-right 5px
  .picture
    width 100%
  .sourceText
    font-style italic
</style>
