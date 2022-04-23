<template>
  <div id="app">
    <div class="head">
      <nav class="menu-nav">
        <router-link to="/">主页</router-link>
        <router-link to="/about">广场</router-link>
        <router-link to="/index">快速匹配</router-link>
        <!-- <router-link to="/about" class="img-border"><img src="../src/assets/logo.png" class="img"></router-link> -->
        <div class="login-border" @mouseover="mouseover" @mouseout="mouseout">
          <img class="login" src="../src/assets/tx.jpg" />
        </div>
      </nav>
    </div>
    <nav
      v-if="!cookice"
      v-show="person_con"
      class="loginout-nav"
      :class="loginout"
      @mouseover="person_infoContinue()"
      @mouseout="cl_person_infoContinue()"
    >
      <h4>欢迎访问胜宝婚介所</h4>
      <p style="font-size: 15px; font-weight: bold; style:; ">请登录</p>
      <hr class="hr" />
      <router-link class="loginout-router-link" to="about">登录</router-link>
    </nav>
    <nav
      v-else
      v-show="person_con"
      class="loginin-nav"
      :class="loginin"
      @mouseover="person_infoContinue()"
      @mouseout="cl_person_infoContinue()"
    >
      <h4>欢迎您，{{ userid }}</h4>
      <hr class="hr" />
      <router-link class="loginin-router-link" to="index">个人设置</router-link>
      <router-link class="loginin-router-link" to="index">账户中心</router-link>
      <div class="loginin-router-link" @click="loginOut">退出登录</div>
    </nav>
    <router-view />
  </div>
</template>


<script>
export default {
  name: "",
  data() {
    return {
      placeholder: "搜索课程",
      token: "", //判断是否登录的参数，在加载主页时直接判断
      person_con: false,
      isperson_infoContinue: true, //增加
      userid: "你好",
      loginin: "",
      loginout: "",
      cookice: true,
    };
  },
  created() {
    this.isToken();
  },
  methods: {
    isToken() {
      if (!localStorage.getItem("token")) {
        this.cookice = false;
        // console.log(this.cookice)
        this.loginin="nodisplay1"
        this.loginout="nodisplay0"
      } else {
        this.cookice = true;
        // console.log(this.cookice)
        this.loginin="nodisplay0"
        this.loginout="nodisplay1"
      }
    },

    //不变
    mouseover() {
      this.person_con = true;
    },
    //增加判断
    mouseout() {
      this.person_con = false;
    },
    person_infoContinue() {
      this.person_con = true;
      this.isperson_infoContinue = true;
    },

    cl_person_infoContinue() {
      this.isperson_infoContinue = false;
      this.person_con = false;
    },
    loginOut() {
      localStorage.removeItem("token");
      this.isToken();
    },
  },
};
</script>


<style lang="scss">
body {
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.head {
  background-color: aliceblue;
  position: fixed;
  z-index: 99;
  width: 100%;
  top: 0%;
}
.menu-nav {
  display: flex;
  height: 50px;

  a {
    font-weight: bold;
    color: #2c3e50;
    text-transform: none;
    margin-left: 40px;
    text-align: center;
    line-height: 50px;
    text-decoration: none;

    &.router-link-exact-active {
      color: #42b983;
      text-decoration: none;
      text-align: center;
    }
    &.router-link {
      text-decoration: none;
    }
  }
}
.hr {
  background-color: rgb(241, 241, 241);
  border: 1px solid rgb(238, 238, 238);
  transform: scale(1, 0.2);
}
.login-border {
  display: flex;
  background: white;
  border: 1px solid rgb(221, 219, 219);
  padding: 1px;
  border-radius: 50%;
  height: 30px;
  margin-top: 10px;
  margin-bottom: 10px;
  position: relative;
  left: 70%;
  z-index: 999;
}
.login {
  border-radius: 50%;
  height: 30px;
  width: 30px;
}
.loginin-nav {
  background-color: white;
  width: 200px;
  border-right: 10%;
  position: fixed;
  z-index: 998;
  top: 44px;
  border-radius: 5px;
  margin-left: 81%;
}
.loginin-router-link {
  cursor: pointer;
  text-decoration: none;
  display: flex;
  padding: 10px;
  margin-left: 55px;
  font-weight: bold;
  color: #6f757c;
}
.loginout-nav {
  background-color: white;
  width: 200px;
  border-right: 10%;
  position: fixed;
  z-index: 998;
  top: 44px;
  border-radius: 5px;
  margin-left: 81%;
}
.loginout-router-link {
  text-decoration: none;
  display: flex;
  padding: 10px;
  text-align: center;
  margin-left: 75px;
  margin-top: -10px;
  font-weight: bold;
  color: #6f757c;
}
p {
  text-align: center;
  margin-top: -20px;
  color: #8e9aaf;
}
h4 {
  color: #8e9aaf;
}
.nodisplay1 {
  display: none;
  transition: all 0.5s ease;
}
.nodiaplay0 {
  
}
</style>
