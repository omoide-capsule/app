<template>
  <v-card>
    <v-card-title>
      <h4>{{ title }}</h4>
    </v-card-title>

    <div
      v-if="image !== ''"
      class="image-box"
      :style="`background-image:url('${image}')`"
    ></div>

    <v-card-text>
      <p>{{ description }}</p>
    </v-card-text>
    <v-card-actions>
      <v-btn color="#ea5550" text>削除</v-btn>
      <v-btn color="green" class="button" @click="$emit('close')">閉じる</v-btn>
    </v-card-actions>
  </v-card>
</template>
<script>
export default {
  props: {
    title: {
      type: String,
      default: ''
    },
    image: {
      type: String,
      default: ''
    },
    description: {
      type: String,
      default: ''
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
  width: 80%;
  height: 150px;
  background-size: cover;

  border-radius: 10px;
}

.button {
  color: #fff !important;
  font-weight: bold;
}
</style>
