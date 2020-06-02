<template>
  <input
    :value="value"
    class="title-input"
    type="text"
    placeholder="タイトル"
    @input="inputHandler"
  />
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
.title-input {
  font-size: 15pt;
  margin: 10px;
  margin-bottom: 15px;
  width: 85%;
}

.title-input {
  box-sizing: border-box;
  padding: 0.3em;
  transition: 0.3s;
  letter-spacing: 1px;
  color: #333333;
  border: none;
  border-bottom: 1px solid #708090;
  text-align: left;
}
</style>
