<template>
  <v-container>
    <v-layout wrap>
      <v-flex align-center>
        <div
          v-if="uploaded"
          :style="`background-image:url(${imgSrc})`"
          class="img-preview"
        >
          <v-btn icon class="remove-button" @click="onRemovePicture">
            <v-icon color="#ffffff">mdi-close-circle</v-icon>
          </v-btn>
        </div>

        <div v-else>
          <label>
            <picture-button />
            <input
              ref="fileInput"
              type="file"
              style="display:none"
              accept="image/*"
              @change="onFileStateChange"
            />
          </label>
        </div>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
import pictureButton from './pictureButton'
export default {
  components: {
    pictureButton
  },
  data() {
    return {
      content: '',
      uploaded: false,
      imgSrc: ''
    }
  },
  methods: {
    onFileStateChange() {
      const inputElm = this.$refs.fileInput
      const files = inputElm.files

      if (files.length < 1) {
        this.uploaded = false
        return 0
      } else {
        this.uploaded = true
        const file = files[0]

        const reader = new FileReader()

        reader.onload = (_e) => {
          this.imgSrc = reader.result
          console.log(this.imgSrc)
          this.$emit('input', this.imgSrc.split(',')[1])
        }

        reader.readAsDataURL(file)
      }
    },
    onRemovePicture() {
      this.imgSrc = ''
      this.uploaded = false
    }
  }
}
</script>
<style>
.img-preview {
  border-radius: 10px;
  height: 30vh;
  position: relative;
  background-size: cover;
}

.remove-button {
  position: absolute;
  top: 10px;
  right: 10px;
}
</style>
