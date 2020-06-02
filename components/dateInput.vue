<template>
  <v-container>
    <v-col>
      <v-row style="padding-bottom:20px;">
        <h4>カプセルが届く日</h4>
      </v-row>
      <v-row>
        <div class="date-box">
          <input
            ref="customdate"
            v-model="customDate"
            :min="minDate"
            type="date"
            :disabled="useRandom"
            class="dateInput"
          />
        </div>
      </v-row>
      <v-row>
        <label>
          <input ref="useRandom" v-model="useRandom" type="checkbox" />
          ランダムな日付を使う (365~1200 days later)
        </label>
      </v-row>
    </v-col>
    <v-divider />
  </v-container>
</template>
<script>
export default {
  data() {
    const today = new Date()
    const yyyy = today.getFullYear()
    const mm = ('0' + (today.getMonth() + 1)).slice(-2)
    const dd = ('0' + today.getDate()).slice(-2)
    const todayStr = yyyy + '-' + mm + '-' + dd

    return {
      useRandom: false,
      customDate: todayStr,
      minDate: todayStr
    }
  }
}
</script>
<style>
.dateInput {
  border-bottom: #aaaaaaa0 solid 0.2px;
  font-size: 20px;
  margin-bottom: 5px;
  color: #555555;
}
.dateInput[disabled] {
  opacity: 0.4;
}

.date-box {
  padding-bottom: 10px;
}
</style>
