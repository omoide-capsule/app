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
            :value="customDate"
            :min="minDate"
            type="date"
            :disabled="useRandom"
            class="dateInput"
            @input="dateListener"
          />
        </div>
      </v-row>
      <v-row>
        <label>
          <input
            ref="useRandom"
            :value="useRandom"
            type="checkbox"
            @input="checkListener"
          />
          ランダムな日付を使う (365~1200 days later)
        </label>
      </v-row>
    </v-col>
    <v-divider />
  </v-container>
</template>
<script>
export default {
  props: { value: { type: String, default: '' } },
  data() {
    const todayStr = this.dateToStr(new Date())
    return {
      useRandom: false,
      customDate: todayStr,
      minDate: todayStr
    }
  },
  methods: {
    randomDay() {
      const randomInt = (Math.random() * 1000) % 835
      return this.dateToStr(
        new Date().setDate(new Date().getDate() + randomInt + 365)
      )
    },
    dateToStr(date) {
      const _date = new Date(date)
      const yyyy = _date.getFullYear()
      const mm = ('0' + (_date.getMonth() + 1)).slice(-2)
      const dd = ('0' + _date.getDate()).slice(-2)
      return yyyy + '-' + mm + '-' + dd
    },
    calculatedValue() {
      const res = this.useRandom ? this.randomDay() : this.customDate
      return res
    },
    dateListener(v) {
      this.customDate = v.target.value
      this.$emit('input', this.calculatedValue())
    },
    checkListener(v) {
      this.useRandom = v.target.checked
      this.$emit('input', this.calculatedValue())
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
