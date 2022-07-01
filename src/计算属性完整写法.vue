<template>
  <div>
    <div>
      <span>姓名:</span>
      <input type="text" v-model="full" />
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    full: {
      set(val) {
        console.log(val);
      },
      get() {
        return '111';
      },
    },
  },
};
</script>

<style></style>
