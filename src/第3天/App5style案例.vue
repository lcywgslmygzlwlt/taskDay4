<template>
  <div>
    <p :style="{ color: 'aqua', fontSize: '90px' }">vue 动态绑定style11</p>
    <p :style="{ color: color3, fontSize: fs }">vue 动态绑定style22</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      color3: 'purple',
      fs: '120px',
    };
  },
  methods: {},
};
</script>

<style></style>
