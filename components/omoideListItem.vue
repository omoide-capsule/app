<template>
  <v-list-item>
    <v-list-item-title>{{ omoide.title }}</v-list-item-title>
    <v-list-item-action>
      <omoide-dialog :omoide="omoide" @deleted="$emit('deleted')" />
    </v-list-item-action>
  </v-list-item>
</template>
<script>
import omoideDialog from '../components/omoideDialog'

export default {
  components: {
    omoideDialog
  },
  props: {
    omoide: {
      type: Object,
      default: () => {
        return { title: '', description: '', UUID: '' }
      }
    }
  }
}
</script>
