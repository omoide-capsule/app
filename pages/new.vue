<template>
  <v-layout column align-center>
    <title-input />
    <picture-input />
    <body-input />
    <post-btn />
  </v-layout>
</template>

<script>
import titleInput from '../components/titleInput'
import bodyInput from '../components/bodyInput'
import pictureInput from '../components/pictureInput'
import postBtn from '../components/postBtn'
export default {
  components: { titleInput, pictureInput, bodyInput, postBtn }
}
</script>
