

<template>
  <v-container>
    <PhotoForm @addPhoto="addPhoto"/>
    <v-row>
      <Photo
          v-for="photo in $store.getters.getAllPhotos" :key="photo.id"
          :photo="photo"
      />
    </v-row>
    <PhotoDialog />

  </v-container>
</template>

<script>
import Photo from "@/components/photo/Photo"
import PhotoForm from "@/components/photo/PhotoForm"
import PhotoDialog from "@/components/photo/PhotoDialog"
import {mapActions} from "vuex"

export default {
  components: {
    Photo, PhotoForm, PhotoDialog
  },
  data: () => ({
    photos: [],
    // currentPhoto: {},
    // dialogVisible: false
  }),
  mounted() {
    this.fetchPhotos()
  },
  methods: {
    ...mapActions(['fetchPhotos']),
    addPhoto(photo){
      this.photos.push(photo)
    },
    openPhoto(photo){
      this.currentPhoto = photo
      this.$store.dispatch("showDialog")
    }
  }
}
</script>

<style scoped>

</style>