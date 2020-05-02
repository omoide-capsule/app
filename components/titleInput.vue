<template>
  <input
    v-model="value"
    class="title-input"
    type="text"
    placeholder="タイトル"
    @change="$emit('input', value)"
  />
</template>
<script>
export default {
  props: ['value']
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
