<template>
  <v-container>
    <v-divider />
    <v-flex xl12>
      <textarea
        :value="value"
        placeholder="この思い出について書く🖋"
        class="omoideBody"
        maxlength="200"
        @input="inputHandler"
      ></textarea>
    </v-flex>
    <v-divider />
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      value: ''
    }
  },
  methods: {
    inputHandler(e) {
      this.value = e.target.value
      this.$emit('input', this.value)
    }
  }
}
</script>
<style>
.omoideBody {
  padding: 10px;
  width: 100%;
  height: 200px;
  resize: none;
}
</style>
