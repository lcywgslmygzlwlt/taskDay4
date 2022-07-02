<template>
  <div>
    <span>全选:</span> <input type="checkbox" v-model="isAll" />
    <button @click="btn">反选</button>
    <ul>
      <li v-for="(item, index) in arr" :key="index">
        <input type="checkbox" v-model="item.c" />
        <span>{{ item.name }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'VuecliDemo13',
  methods: {
    btn() {
      this.arr.forEach((ele) => (ele.c = !ele.c));
    },
  },
  data() {
    return {
      arr: [
        {
          name: '猪八戒',
          c: false,
        },
        {
          name: '孙悟空',
          c: false,
        },
        {
          name: '唐僧',
          c: false,
        },
        {
          name: '白龙马',
          c: false,
        },
      ],
    };
  },
  computed: {
    isAll: {
      get() {
        return this.arr.every((ele) => ele.c);
      },
      set(value) {
        return this.arr.forEach((ele) => (ele.c = value));
      },
    },
  },
};
</script>

<style lang="scss" scoped></style>
