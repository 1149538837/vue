<template>
  <div class="background">
    <div class="accordion">
      <div class="images">
        <div
          class="box"
          :class="eleindex == index ? 'index' : ''"
          v-for="(images, index) in piclist"
          :key="index"
          @mouseenter="enter(index)"
          @mouseleave="out"
        >
          <img :src="images.img" />
          <div class="box-footer" :style="{ height: ee + 'px' }">
            <div style="display: flex">
              <div class="user-name">蔡望胜</div>
              <div
                class="user-moretext"
                :style="{ transform: 'rotate(' + trun + 'deg)' }"
                @click="tomore"
              >
                >
              </div>
            </div>
            <div class="user-text" :style="{ height: moretext + 'px' }">
              大家好，我的名字叫菜旺胜，19岁。 住在机电北部的别墅区8号，未婚。
              每天都要上课到下午5点才回家。 不抽烟，喝酒也仅仅止于品尝。
              晚上11点睡，每天要睡足7个小时。
              睡前，我一定喝一杯温牛奶，然后做20分钟的健身操，上了床，马上熟睡。一觉到天亮，决不把疲劳和压力留到第二天。
              我最大的爱好就是过平静的生活，我把我的细节都放在跟别人对线上，我会铲除所有与我抗衡的敌人，这样才能使我安心入眠。
            </div>
            <div class="button-footer">
              <button class="user-button">聊聊</button>
              <button class="user-button">个人主页</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
 
<script>
export default {
  data() {
    return {
      timer: null,
      more: false,
      ee: 200, //信息框高度
      trun: -90, //旋转角度
      moretext: 45, //自我介绍高度
      eleindex: 0, //主页
      piclist: [
        { img: require("../assets/tx.jpg") },
        { img: require("../assets/tx.jpg") },
        { img: require("../assets/tx.jpg") },
        { img: require("../assets/tx.jpg") },
        { img: require("../assets/tx.jpg") },
        { img: require("../assets/tx.jpg") },
      ],
    };
  },
  created() {
    clearInterval(this.timer);
    this.timer = null;
    this.timer = setInterval(() => {
      this.eleindex++;
      if (this.eleindex == 6) {
        this.eleindex = 0;
      }
    }, 5000);
  },
  methods: {
    enter(index) {
      this.eleindex = index;
      clearInterval(this.timer);
    },
    out() {
      this.more = false;
      this.ee = 200;
      this.trun = -90;
      this.moretext = 45;
      this.timer = setInterval(() => {
        this.eleindex++;
        if (this.eleindex == 6) {
          this.eleindex = 0;
        }
      }, 5000);
    },
    tomore() {
      if (this.more == false) {
        this.ee = 400;
        this.trun = 90;
        this.moretext = 90;
        this.more = true;
      } else {
        this.ee = 200;
        this.trun = -90;
        this.moretext = 45;
        this.more = false;
      }
    },
  },
};
</script>
<style>
.background {
  background-color: #cbc0d3;
  border: 0px;
  border-radius: 20px;
}
.accordion {
  border: 1px solid white;
  border-radius: 30px 30px 0px 0px;
  background: white;
  margin: 80px 30px 0px 30px;
  padding: 4% 2%;
}
.images {
  display: flex;
  width: 800px;

  box-sizing: border-box;
  border: 1px solid black;
  height: 400px;
}
.images:before {
  background-color: rgba(0, 0, 0, 0.4);
}

.box {
  flex: 1;
  overflow: hidden;
  transition: 0.5s;
  box-shadow: 0 20px 30px rgba(0, 0, 0, 0.1);
  position: relative;
  margin: 5px;
  border-radius: 20px;
}

.box > img {
  width: 100%;
  height: 100%;
  -o-object-fit: cover;
  object-fit: cover;
  transition: 0.5s;
}

.index {
  flex: 1 1 50%;
}

.index > img {
  width: 100%;
  height: 100%;
}
.box:hover .box-footer {
  opacity: 1;
  transform: translateY(0);
  transition-delay: 0.3s;
}
.box-footer {
  position: absolute;
  bottom: -20px;
  border-bottom-left-radius: 30px;
  border-bottom-right-radius: 30px;
  color: rgba(255, 255, 255, 0.8);
  background: rgba(34, 34, 34, 0.35);
  padding: 0;
  text-align: center;
  overflow: hidden;
  width: 100%;
  box-sizing: border-box;
  opacity: 0;
  transition: 0.3s;
  transform: translateY(100%);
}
.user-name {
  font-size: 24px;
  margin: 10px 0px 0px;
  font-weight: bold;
  color: #eac7cc;
  margin-left: 191.75px;
}

.user-text {
  padding: 10px;
  font-size: 18px;
  overflow: hidden;
  transition: 0.3s;
  transition-delay: 0.3s;
}

.user-moretext {
  margin-top: 10px;
  margin-left: 150px;
  font-size: 34px;
  font-weight: bolder;
  font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  color: #a2a1a1;
  opacity: 0.8;
  cursor: pointer;
  transition: 0.3s;
}
.user-button {
  width: 150px;
  height: 45px;
  margin: 20px 20px 20px 45px;
  border: 2px solid #a2a1a1;
  background: #cccccc;
  border-radius: 20px;
  font-size: 18px;
  color: #000000d1;
  opacity: 0.8;
  font-weight: bold;
}
.user-button:hover {
  background: #a2a1a1;
}
.button-footer {
  position: fixed;
  bottom: 10px;
}
</style>


