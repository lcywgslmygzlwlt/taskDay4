<template>
  <div id="app">
    <table class="tb">
      <tr>
        <th><input type="checkbox" v-model="isAll" />全选</th>
        <th>商品</th>
        <th>单价</th>
        <th>数量</th>
        <th>小记</th>
        <th>操作</th>
      </tr>
      <!-- 循环渲染的元素tr -->
      <tr v-for="obj in list" :key="obj.id">
        <td><input type="checkbox" v-model="obj.fl" /></td>
        <td>{{ obj.name }}</td>
        <td>{{ obj.price }}</td>
        <td>
          <button @click="obj.num <= 0 ? (obj.num = 0) : obj.num--">-</button
          ><input
            type="text"
            v-model="obj.num"
            style="text-align: center"
          /><button @click="obj.num++">+</button>
        </td>
        <td>{{ (obj.count = obj.price * obj.num) }}</td>
        <td><button @click="del(obj.id)">删除</button></td>
      </tr>

      <tr v-if="list.length === 0">
        <td colspan="4">没有数据咯~</td>
      </tr>
    </table>

    <br />
    <button @click="delIsTrue()">删除选中商品</button>
    <button @click="delAll">清理购物车</button>
    <br />
    <div style="margin-top: 20px">
      <h2>统计</h2>
      <p>已经选中商品件数{{ sum }}</p>
      <p>总价{{ allSum }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [
        { id: 1, name: '奔驰', price: 100, num: 0, count: 0, fl: false },
        { id: 2, name: '宝马', price: 120, num: 0, count: 0, fl: false },
        { id: 3, name: '奥迪', price: 140, num: 0, count: 0, fl: false },
      ],
    };
  },
  methods: {
    del(id) {
      // 删除按钮 - 得到索引, 删除数组里元素
      const index = this.list.findIndex((item) => item.id == id);
      this.list.splice(index, 1);
    },
    delIsTrue() {
      const newArr = this.list.filter((ele) => ele.fl == false);
      this.list = newArr;
    },
    delAll() {
      this.list = [];
      this.isAll = false;
    },
  },

  computed: {
    isAll: {
      set(val) {
        this.list.forEach((item) => (item.fl = val));
      },
      get() {
        return this.list.length == 0
          ? false
          : this.list.every((item) => item.fl);
      },
    },
    sum() {
      return this.list
        .filter((ele) => ele.fl == true)
        .reduce((sum, next) => (sum = sum + next.num), 0);
    },
    allSum() {
      return this.list
        .filter((ele) => ele.fl == true)
        .reduce((val, next) => (val += next.num * next.count), 0);
    },
  },
  watch: {
    list: {
      handler(newVal) {
        newVal.forEach((item) => {
          if (item.num < 0) {
            alert('不能输入负值！');
            item.num = 0;
          }
        });
        // console.log(newVal);
      },
      deep: true,
      // immediate: true,
    },
  },
};
</script>
<style>
#app {
  width: 600px;
  margin: 10px auto;
}

.tb {
  border-collapse: collapse;
  width: 100%;
}

.tb th {
  background-color: #0094ff;
  color: white;
}

.tb td,
.tb th {
  padding: 5px;
  border: 1px solid black;
  text-align: center;
}

.add {
  padding: 5px;
  border: 1px solid black;
  margin-bottom: 10px;
}
</style>
