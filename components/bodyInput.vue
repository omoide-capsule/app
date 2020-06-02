<template>
  <v-container>
    <v-divider />
    <v-flex xl12>
      <textarea
        :value="value"
        placeholder="この思い出について書く🖋"
        class="omoideBody"
        @input="$emit('input', value)"
        maxlength="200"
      ></textarea>
    </v-flex>
    <v-divider />
  </v-container>
</template>
<script>
export default {
  props: ['value']
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
