<template>
  <v-container>
    <v-divider />
    <v-flex xl12>
      <textarea
        v-model="content"
        placeholder="この思い出について書く🖋"
        class="omoideBody"
      ></textarea>
    </v-flex>
    <v-divider />
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      content: ''
    }
  }
}
</script>
<style>
.omoideBody {
  padding: 10px;
  width: 100%;
  height: 200px;
}
</style>
