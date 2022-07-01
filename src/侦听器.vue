<template>
  <div>
    <input type="text" v-model="name" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
    };
  },
  watch: {
    // 新newVal，旧oldVal
    name(newVal, oldVal) {
      console.log(newVal, oldVal);
    },
  },
};
</script>

<style></style>
