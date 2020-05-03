<template>
  <v-container>
    <v-flex xl12>
      <div v-if="uploaded"></div>
      <div v-else>
        <label>
          <picture-button />
          <input
            type="file"
            ref="fileInput"
            style="display:none"
            accept="image/*"
          />
        </label>
      </div>
    </v-flex>
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
      uploaded: false
    }
  }
}
</script>
