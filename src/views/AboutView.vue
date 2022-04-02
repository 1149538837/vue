<template>
  <div class="about">
    <div class="container">
      <div class="welcome">
        <div :class="pinkbox">
          <!-- 注册 -->
          <div class="signup nodisplay">
            <h1>快速注册</h1>
            <form autocomplete="off" method="post">
              <input type="text" name="username" placeholder="账号" />
              <input type="email" name="email" placeholder="邮箱" />
              <input type="password" name="password1" placeholder="密码" />
              <input type="password" name="password2" placeholder="重复密码" />
              <!-- @if(session()->has('errors'))
                        <li class="errors" style="margin-top: 10px">{{session()->get('errors')}}</li>
                    @endif
                    {!! csrf_field() !!} -->
              <button class="button sumbit" style="margin-top: 43px">
                注册
              </button>
            </form>
          </div>

          <!-- 登录 -->
          <div class="signin">
            <h1>快速登录</h1>
            <form class="more-padding" autocomplete="off" method="post">
              <input type="username" name="username" placeholder="账号" />
              <input type="password" name="password" placeholder="密码" />
              <div style="display: flex">
                <input
                  type="text"
                  name="code"
                  placeholder="验证码"
                  style="
                    width: 100px;
                    height: 40px;
                    padding: 0px;
                    text-indent: 10px;
                    margin-left: 15px;
                    margin-top: 10px;
                  "
                />
                <img
                  src="../assets/tb.png"
                  style="
                    width: 200px;
                    height: 50px;
                    margin-top: 10px;
                    margin-left: -20px;
                  "
                />
              </div>
              <!-- @if(session()->has('error'))
                        <li class="errors" style="">{{session()->get('error')}}</li>
                    @endif -->
              <div class="checkbox">
                <input type="checkbox" id="remember" /><label for="remember"
                  >记住我</label
                >
              </div>
              <button class="button sumbit" onclick="">登录</button>
            </form>
          </div>
        </div>

        <div class="leftbox">
          <h2 class="title"><span>查询</span>&购票</h2>
          <p class="desc">我们要做最好的 <span>购票网站</span></p>
          <img class="flower smaller" src="../assets/login.jpg" />
          <p class="account">已经有账号了？</p>
          <button class="button" id="signin" @click="sigin">登录</button>
        </div>

        <div class="rightbox">
          <h2 class="title"><span>电影</span>&演出</h2>
          <p class="desc">我们有最全的 <span>电影</span></p>
          <img class="flower" src="../assets/login.jpg" />
          <p class="account">还没有注册？</p>
          <button class="button" id="signup" @click="signup">注册</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
    data() {
      return {
        pinkbox: "pinkbox0",
      };
    },
    methods: {
    signup() {
      this.pinkbox = "pinkbox1";
    },

    sigin() {
        this.pinkbox = "pinkbox0";
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Open+Sans:300,400|Lora");

body {
  background: #cbc0d3;
}
.container {
  margin: auto;
  width: 800px;
  height: 450px;
  position: relative;
}

.welcome {
  background: #f6f6f6;
  width: 850px;
  height: 500px;
  position: absolute;
  top: 25%;
  border-radius: 5px;
  box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.1);
}

.pinkbox1 {
  position: absolute;
  top: -5%;
  left: 5%;
  background: #eac7cc;
  width: 380px;
  height: 550px;
  border-radius: 5px;
  box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
  transition: all 0.5s ease-in-out;
  z-index: 2;
  transform: translateX(100%);
}
.pinkbox0 {
  position: absolute;
  top: -5%;
  left: 5%;
  background: #eac7cc;
  width: 380px;
  height: 550px;
  border-radius: 5px;
  box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
  transition: all 0.5s ease-in-out;
  z-index: 2;
  transform: translateX(0%);
}

.nodisplay {
  display: none;
  transition: all 0.5s ease;
}

.leftbox,
.rightbox {
  position: absolute;
  width: 50%;
  transition: 1s all ease;
}

.leftbox {
  left: -0%;
}

.rightbox {
  right: -0%;
}

h1 {
  font-family: "Open Sans", sans-serif;
  text-align: center;
  margin-top: 95px;
  text-transform: uppercase;
  color: #f6f6f6;
  font-size: 40px;
  letter-spacing: 8px;
  margin-bottom: 30px;
}

.title {
  font-family: "Lora", serif;
  color: #8e9aaf;
  font-size: 2.5em;
  line-height: 1.1em;
  letter-spacing: 3px;
  text-align: center;
  font-weight: 350;
  margin-top: 15%;
}

.desc {
  margin-top: -8px;
  font-size: 15px;
}

.account {
  margin-top: 50%;
  font-size: 15px;
}

p {
  font-family: "Open Sans", sans-serif;
  font-size: 0.7em;
  letter-spacing: 2px;
  color: #8e9aaf;
  text-align: center;
}

span {
  color: #eac7cc;
}

.flower {
  position: absolute;
  width: 200px;
  height: 180px;
  top: 40%;
  left: 27%;
  opacity: 0.8;
}

.smaller {
  width: 200px;
  height: 180px;
  top: 40%;
  left: 27%;
  opacity: 0.9;
}

button {
  width: 200px;
  padding: 10px;
  font-family: "Open Sans", sans-serif;
  text-transform: uppercase;
  letter-spacing: 3px;
  font-size: 18px;
  border-radius: 10px;
  margin: auto;
  outline: none;
  display: block;
}

button:hover {
  background: #eac7cc;
  color: #f6f6f6;
  transition: background-color 1s ease-out;
}

.button {
  margin-top: 3%;
  background: #f6f6f6;
  color: #ce7d88;
  border: solid 1px #eac7cc;
}

form {
  display: flex;
  align-items: center;
  flex-direction: column;
  padding-top: 7px;
}

.more-padding {
  padding-top: 0px;
}

.more-padding input {
  padding: 10px;
}

.more-padding .sumbit {
  margin-top: 45px;
}

.sumbit {
  margin-top: 25px;
  border-color: white;
}

.sumbit:hover {
  background: #cbc0d3;
  border-color: #bfb1c9;
}

input {
  background: #eac7cc;
  width: 65%;
  color: #ce7d88;
  border: none;
  border-bottom: 1px solid rgba(246, 246, 246, 0.5);
  padding: 9px;
  font-weight: 100;
  margin-top: 10px;
}

input::placeholder {
  color: #f6f6f6;
  letter-spacing: 2px;
  font-size: 1em;
  font-weight: 100;
}

input:focus {
  color: #ce7d88;
  outline: none;
  border-bottom: 1.2px solid rgba(206, 125, 136, 0.7);
  font-size: 1em;
  transition: 0.8s all ease;
}

input:focus::placeholder {
  opacity: 0;
}

label {
  font-family: "Open Sans", sans-serif;
  color: #ce7d88;
  font-size: 0.8em;
  letter-spacing: 1px;
  margin-top: 8px;
}

.checkbox {
  display: flex;
  white-space: nowrap;
  position: relative;
  top: 5px;
  left: -65px;
  zoom: 120%;
}
.errors {
  color: #ce7d88;
  font-size: 14px;
  position: relative;
  left: -60px;
}
input[type="checkbox"] {
  width: 15px;
  background: #ce7d88;
}

.checkbox input[type="checkbox"]:checked + label {
  color: #ce7d88;
  transition: 0.5s all ease;
}
</style>