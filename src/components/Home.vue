<template>
<div>
  <q-carousel arrows dots autoplay infinite style="width: 100%;">

    <div slot="slide"
     v-for="(picture, index) of carouselPictures"
     :key="index"
     class="bg-tertiary centered">
     <router-link :to="{ path: 'plant', query: { name: picture.name } }">
      <img :src="picture.path" style="width: 100%; max-height: 500px;" />
     </router-link>
    </div>

  </q-carousel>

  <div class="col-xs-12" style="margin: 20px;">
    {{ homeText }}
  </div>
</div>
</template>

<script>
import { QCarousel } from 'quasar'

export default {
  components: {
    QCarousel
  },
  data () {
    return {
      carouselPictures: this.siteData.home.carouselPictures,
      homeText: this.siteData.home.text
    }
  }
}
</script>

<style>

</style>
