<template>
  <div>
    <p>原来的样子: {{ msg }}</p>
    <!-- 2. 过滤器使用
      语法: {{ 值 | 过滤器名字 }}
     -->
    <p :title="msg | toUp">使用翻转过滤器: {{ msg | tuUp | toReverse }}</p>
    <p :title="msg | toUp">鼠标长停</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      msg: 'hello world',
    };
  },
  filters: {
    toUp(val) {
      console.log(val);
      return val.toUpperCase();
    },
  },
};
</script>

<style></style>
