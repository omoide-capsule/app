<template>
  <v-layout column align-center>
    <title-input v-model="title" />
    <picture-input v-model="picture" />
    <body-input v-model="body" />
    <date-input ref="dateInput" v-model="date" />
    <post-btn @click="createCapsule" />
  </v-layout>
</template>

<script>
import axios from 'axios'
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
      date: '', // This will overwitten at mounted()
      id: null
    }
  },
  mounted() {
    this.date = this.$refs.dateInput.dateToStr(new Date())

    window.liff
      .init({
        liffId: process.env.LIFFId
      })
      .then(() => {
        // start to use LIFF's api
        this.initApp()
      })
  },
  methods: {
    createCapsule() {
      const deliveryDate = new Date(this.date)
      deliveryDate.setHours(0)
      deliveryDate.setMinutes(0)

      if (this.title === '') {
        window.alert('タイトルは必須項目です')
        return
      }
      if (this.image === '') {
        window.alert('画像の添付は必須です。')
        return
      }
      const capsule = {
        id: this.id, // this.id,
        title: this.title,
        description: this.body,
        registeredDate: Math.floor(new Date().getTime() / 1000),
        deliveryDate: Math.floor(deliveryDate.getTime() / 1000),
        image: this.picture
      }

      axios
        .post(`${process.env.apiBaseUrl}/capsule`, capsule)
        .then((res) => {
          console.log('Capsule Registerd')
        })
        .catch((err) => {
          window.alert(JSON.stringify(err))
        })
    },
    initApp() {
      const ctx = window.liff.getContext()
      this.id = ctx.utouId || ctx.groupId || ctx.roomId || ctx.userId
    }
  },
  head() {
    return {
      titleTemplate: '',
      title: 'あたらしいカプセルをつくる',
      script: [{ src: 'https://static.line-scdn.net/liff/edge/2/sdk.js' }]
    }
  }
}
</script>
