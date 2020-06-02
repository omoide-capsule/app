<template>
  <v-layout column align-center>
    <title-input />
    <picture-input />
    <body-input />
    <date-input />
    <post-btn />
  </v-layout>
</template>

<script>
import titleInput from '../components/titleInput'
import bodyInput from '../components/bodyInput'
import pictureInput from '../components/pictureInput'
import dateInput from '../components/dateInput'
import postBtn from '../components/postBtn'

export default {
  components: { titleInput, pictureInput, bodyInput, dateInput, postBtn }
}
</script>
