<template>
  <div>
    <h4>{{ msg | count('万') }}</h4>
    <hr />
    <h4>{{ msg | count('千') }}</h4>
    <hr />
    <h4>{{ msg | dates('-') }}</h4>
    <hr />
    <h4>{{ msg | dates('/') }}</h4>
  </div>
</template>

<script>
import moment from 'moment';

export default {
  data() {
    return {
      msg: 1876986,
    };
  },
  methods: {},
  filters: {
    count(a, b) {
      if (b == '万') {
        return a / 10000 + '万';
      } else {
        return a / 1000 + '千';
      }
    },
    dates(val, s) {
      const data = new Date(val);
      console.log(data);
      if (s == '-') {
        return moment(val).format('YYYY-MM-DD');
      } else {
        return moment(val).format('YYYY/MM/DD');
      }
    },
  },
};
</script>

<style></style>
