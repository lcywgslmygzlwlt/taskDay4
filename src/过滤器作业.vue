<template>
  <div>
    <h2>国内网站：粉丝数量：{{ time | timeFmtTime) }}</h2>

    <h2>外内网站：粉丝数量：{{ time | time1FmtTime }}</h2>

    <!-- <h3>时间：{{ time1 | time3FmtTime }}</h3>

    <h3>时间：{{ time1 | time4FmtTime }}</h3> -->
  </div>
</template>

<script>
import moment from 'moment'
export default {
  data() {
    return {
      time: 1876986,
      // time1: 1636450540055,
    }
  },
  filters: {
    timeFmtTime(val) {
      return moment(val) / 1000 + '千'
    },
    time1FmtTime(val) {
      return moment(val) / 1000 + '千'
    },
    filters: {
      change(val, arg1) {
        if (arg1 == 'home') {
          return val / 10000 + '万'
        } else {
          return val / 1000 + '千'
        }
      },
      beijingTime(val, arg1) {
        const date = new Date(val)
        return moment(date).format('YYYY-MM-DD').replace(/\D/g, arg1)
      },
    },
  },
}
</script>

<style></style>
