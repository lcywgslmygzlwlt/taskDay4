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
      <tr v-for="item in list" :key="item.id">
        <td><input type="checkbox" v-model="item.c" />{{ item.id }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.price }}</td>
        <td>
          <button
            @click.prevent="+item.num <= 0 ? (item.num = 0) : +item.num--"
          >
            -
          </button>
          <input
            style="text-align: center"
            type="text"
            v-model.number="item.num"
            :value="aaaa"
          />
          <button @click.prevent="+item.num++">+</button>
        </td>
        <td>{{ item.price * item.num }}</td>
        <td><button @click="del(item.id)">删除</button></td>
      </tr>

      <tr v-if="list.length === 0">
        <td colspan="4">没有数据咯~</td>
      </tr>
    </table>
    <br />
    <button @click="clearNum">删除选中商品</button>
    <button @click="clearAll">清理购物车</button>
    <br />
    <div style="margin-top: 20px">
      <h2>统计</h2>
      <p>已经选中商品件数:{{ allNum }}</p>
      <p>总价:{{ allPrice }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [
        { id: 1, name: '奔驰', price: 3000, num: 0, c: false },
        { id: 2, name: '宝马', price: 2000, num: 0, c: false },
        { id: 3, name: '奥迪', price: 1000, num: 0, c: false },
      ],
      allNum: 0,
      allPrice: 0,
    };
  },
  methods: {
    del(id) {
      // 删除按钮 - 得到索引, 删除数组里元素
      const index = this.list.forEach((obj) => obj.id == id);
      this.list.splice(index, 1);
    },
    clearNum() {
      this.list = this.list.filter((item) => {
        return !item.c;
      });
    },
    clearAll() {
      this.list = this.list.filter((item) => {
        return item.id > 999;
      });
    },
  },
  computed: {
    isAll: {
      set(val) {
        this.list.forEach((ele) => (ele.c = val));
      },
      get() {
        return this.list.length === 0
          ? false
          : this.list.every((ele) => ele.c == true);
      },
      allNum() {
        return this.list
          .filter((item) => item.c == true)
          .reduce((t, item) => (t += item.num), 0);
      },
      allPrice() {
        return this.list
          .filter((item) => item.c == true)
          .reduce((total, item) => (total += item.num * item.price), 0);
      },
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
