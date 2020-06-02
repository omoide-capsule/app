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
      date: '' // This will overwitten at mounted()
    }
  },
  mounted() {
    this.date = this.$refs.dateInput.dateToStr(new Date())
  },
  methods: {
    createCapsule() {
      const deliveryDate = new Date(this.date)
      deliveryDate.setHours(0)
      deliveryDate.setMinutes(0)

      const capsule = {
        title: this.title,
        description: this.body,
        image: this.picture,
        registeredDate: Math.floor(new Date().getTime() / 1000),
        deliveryDate: Math.floor(deliveryDate.getTime() / 1000)
      }

      console.log(capsule)
    }
  },
  head() {
    return {
      titleTemplate: '',
      title: 'あたらしいカプセルをつくる'
    }
  }
}
</script>
