<template>
  <div>
    <h2>国内网站：粉丝数量：{{ num | changeNum('numa') }}</h2>
    <h2>国外网站：粉丝数量：{{ num | changeNum('numb') }}</h2>
    <h3>国内时间 {{ time | changeTime('-') }}</h3>
    <h3>国外时间 {{ time | changeTime('/') }}</h3>
  </div>
</template>

<script>
import moment from 'moment';
export default {
  data() {
    return {
      num: 1876986,
      time: 1636450540055,
    };
  },
  filters: {
    changeNum(val, arr) {
      if (arr == 'numa') {
        return val / 10000 + '万';
      } else {
        return val / 1000 + '千';
      }
    },
    changeTime(val, str) {
      const date = new Date(val);
      return moment(date).format('YYYY-MM-DD').replace(/\D/g, str);
    },
  },
};
</script>

<style></style>
