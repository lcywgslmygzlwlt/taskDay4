<template>
    <div>
      <h2>国内网站：粉丝数量：{{ num | change("home") }}</h2>
      <h2>外内网站：粉丝数量：{{ num | change("abroad") }}</h2>
      <h3>时间：{{ time1 | time2("-") }}</h3>
      <h3>时间：{{ time1 | time2("/") }}</h3>
    </div>
</template>

<script>
import moment from "moment";
export default {
  data() {
    return {
      num: 1876986,
      time1: 1636450540055,
    };
  },
  filters: {
    change(val, arg1) {
      if (arg1 == "home") {
        return val / 10000 + "万";
      } else {
        return val / 1000 + "千";
      }
    },
    time2(val, arg1) {
      const date = new Date(val);
      return moment(date).format("YYYY-MM-DD").replace(/\D/g, arg1);
    },
  },
};
</script>
<style>
</style>