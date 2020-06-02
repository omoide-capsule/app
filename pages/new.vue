<template>
  <v-layout column align-center>
    <title-input v-model="title" />
    <picture-input v-model="picture" />
    <body-input v-model="body" />
    <date-input v-model="date" />
    <post-btn @click="createCapsule" />
  </v-layout>
</template>

<script>
import titleInput from '../components/titleInput'
import bodyInput from '../components/bodyInput'
import pictureInput from '../components/pictureInput'
import dateInput from '../components/dateInput'
import postBtn from '../components/postBtn'

export default {
  components: { titleInput, pictureInput, bodyInput, dateInput, postBtn },
  data() {
    return {
      title: '',
      picture: '',
      body: '',
      date: ''
    }
  },
  head() {
    return {
      titleTemplate: '',
      title: 'あたらしいカプセルをつくる'
    }
  },
  methods: {
    createCapsule() {
      console.log('cupsule creation!')
    }
  }
}
</script>
