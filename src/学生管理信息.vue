<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model="name" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model="age" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="btn">{{isvalue? '添加':'编辑'}}</button>
    </div>
    <div>
      <table border="1" cellpadding="10" cellspacing="0">
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="(item, index) in newarr" :key="index">
          <td>{{ index + 1 }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>
          <td>
            <button @click="del(item.name)">删除</button>
            <button @click="bian(index)">编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: '',
      age: '',
      sex: '',
      newarr: [],
      newobj: {},
      isvalue: true,
      qqq: 0,
    };
  },
  methods: {
    btn() {
      if (this.isvalue) {
        if (this.name === '' || this.age === '' || this.sex === '') {
          return alert('请重新输入');
        }
        this.newobj = {
          name: this.name,
          age: this.age,
          sex: this.sex,
        };
        this.newarr.push(this.newobj);
        this.name = '';
        this.age = '';
        this.sex = '';
        console.log(this.newarr);
      } else {
        this.newarr[this.qqq].name = this.name;
        this.newarr[this.qqq].age = this.age;
        this.newarr[this.qqq].sex = this.sex;
      }
    },
    del(val) {
      const index = this.newarr.findIndex((ele) => {
        return ele.name == val;
      });
      this.newarr.splice(index, 1);
    },
    bian(id) {
      this.qqq = id;
      this.isvalue = false;
      this.name = this.newarr[id].name;
      this.age = this.newarr[id].age;
      this.sex = this.newarr[id].sex;
    },
  },
};
</script>
