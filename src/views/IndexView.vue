<template>
  <div class="index">
    <h1>This is my first vue demo!</h1>
    <div v-for="item in data" :key="item.id">
      {{ item }}
    </div>
    <div>
      <input type="number" placeholder="username" v-model="username" />
      <input type="number" placeholder="password" v-model="password" />
      <input type="email" placeholder="email" v-model="email" />
      <button @click="add">添加</button>
      <!-- <button @click="update">修改</button> -->
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "IndexView",
  data() {
    return {
      data: [],
      username: "",
      password: "",
      email: "",
    };
  },
  created() {
    this.$axios.get("http://127.0.0.1:8001/select").then((res) => {
      console.log(res);
      this.data = res.data;
    });
  },
  methods: {
    add: function () {
      // axios({
      //   url: "http://127.0.0.1:8001/add",
      //   method: "post",
      //   data: {
      //     username: this.username,
      //     password: this.password,
      //     email: this.email,
      //   },
      //   //将json数据转化为表单数据
      //    transformRequest: [
      //     function (data) {
      //       console.log(this.data)
      //       let ret = "";
      //       for (let it in data) {
      //         ret +=
      //           encodeURIComponent(it) +
      //           "=" +
      //           encodeURIComponent(data[it]) +
      //           "&";
      //       }
      //       return ret;
      //     },
      //   ], 
      //   headers: { "Content-Type": "application/x-www-form-urlencoded" },
      // });
    },
  },
};
</script>

<style lang="scss" scoped>
h1 {
  color: aquamarine;
}
</style>


