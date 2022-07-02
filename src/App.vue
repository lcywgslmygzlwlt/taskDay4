<template>
  <div>
    <h2>国内网站：粉丝数量：{{ num | kiss }}</h2>

    <h2>外内网站：粉丝数量：{{ num | kiss1 }}</h2>

    <h3>时间：{{ time1 | kiss3 }}</h3>

    <h3>时间：{{ time1 | kiss4 }}</h3>
  </div>
</template>

<script>
import moment from 'moment';
// import moment from 'moment';
export default {
  data() {
    return {
      num: 1876986,
      time1: 1636450540055,
    };
  },
  filters: {
    kiss(val) {
      return moment(val) / 10000 + '万';
    },
    kiss1(val) {
      return moment(val) / 1000 + '千';
    },
    kiss3(val) {
      return moment(val).format('yyyy-MM-DD');
    },
    kiss4(val) {
      return moment(val).format('yyyy/MM/DD');
    },
  },
};
</script>

<style></style>
