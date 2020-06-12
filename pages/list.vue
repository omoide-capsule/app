<template>
  <article>
    <v-layout column align-center>
      <v-container>
        <v-row>
          <v-col>
            <h3 style="color:#fff;font-weight:bold;color:#3b5f8a">
              登録済みカプセル
            </h3>
          </v-col>
        </v-row>
        <v-row justify="center">
          <v-col cols="10">
            <v-list>
              <omoide-list-item
                v-for="omoide in omoides"
                :key="omoide.UUID"
                :omoide="omoide"
                @deleted="reflesh"
              />
            </v-list>
            <p class="total-number">
              登録済みのカプセル {{ omoides.length }}件
            </p>
          </v-col>
        </v-row>
      </v-container>
    </v-layout>
  </article>
</template>
<script>
import axios from 'axios'
import omoideListItem from '@/components/omoideListItem'
export default {
  components: { omoideListItem },
  data() {
    return {
      dialog: false,
      omoides: [],
      id: ''
    }
  },
  mounted() {
    this.reflesh()
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
    reflesh() {
      axios
        .get(`${process.env.apiBaseUrl}/capsule?id=${this.id}`)
        .then((res) => {
          console.log(res)
          this.omoides = res.data.Items
        })
        .catch((err) => {
          window.alert(JSON.stringify(err))
          this.omoides = []
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
      title: '登録済みのカプセル',
      script: [{ src: 'https://static.line-scdn.net/liff/edge/2/sdk.js' }]
    }
  }
}
</script>
<style>
.total-number {
  font-size: 12px;
  color: #555555;
  text-align: center;
}
</style>
