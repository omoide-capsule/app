<template>
  <v-card>
    <v-card-title>
      <h4>{{ omoide.title }}</h4>
    </v-card-title>

    <div class="image-box" :style="`background-image:url('${imageUrl}')`"></div>

    <v-card-text align="center">
      <p>{{ omoide.description }}</p>
    </v-card-text>
    <v-card-actions>
      <v-btn color="#ea5550" text @click="deleteCapsule">削除</v-btn>
      <v-btn color="green" class="button" @click="$emit('close')">閉じる</v-btn>
    </v-card-actions>
  </v-card>
</template>
<script>
import axios from 'axios'
export default {
  props: {
    omoide: {
      type: Object,
      default: () => {
        return { title: '', description: '', UUID: '' }
      }
    }
  },
  data() {
    return {
      imageUrl: `${process.env.imageBaseUrl}${this.omoide.UUID}.jpeg`
    }
  },
  methods: {
    deleteCapsule() {
      axios
        .delete(
          `${
            process.env.apiBaseUrl
          }/capsule?id=${'C4bd846c8238a1bed0b2a1dc50057e753'}&UUID=${
            this.omoide.UUID
          }`
        )
        .then((res) => {
          this.$emit('close')
          this.$emit('deleted')
        })
    }
  }
}
</script>
<style scpoped>
.card header {
  border-bottom: #3b5f8a dotted 1px;
}

.image-box {
  margin-left: auto;
  margin-right: auto;
  margin-top: 15px;
  margin-bottom: 15px;
  width: 500px;
  height: 300px;
  background-size: cover;

  border-radius: 10px;
}

.button {
  color: #fff !important;
  font-weight: bold;
}
</style>
