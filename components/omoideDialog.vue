<template>
  <v-dialog v-model="dialog">
    <template v-slot:activator="{ on, attrs }">
      <v-btn v-bind="attrs" icon v-on="on">
        <v-icon>mdi-dots-horizontal</v-icon>
      </v-btn>
    </template>
    <omoide-card
      :omoide="omoide"
      @close="dialog = false"
      @deleted="$emit('deleted')"
    />
  </v-dialog>
</template>
<script>
import omoideCard from './omoideCard'
export default {
  components: {
    omoideCard
  },
  props: {
    omoide: {
      type: Object,
      default: () => {
        return { title: '', description: '', UUID: '' }
      }
    }
  },
  data() {
    return { dialog: false }
  }
}
</script>
