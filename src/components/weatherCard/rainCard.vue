<template>
  <div class="card">
    <div class="card-color" :class="weatherBackgroundClass">
      <div :class="weatherClass"></div>
    </div>
    <div class="card-info">
      <!-- <p>温度</p> -->
      <p>{{info.wendu}} &#176;C  {{info.tq}}</p>
      <p>{{info.max}} &#176;C - {{info.min}} &#176;C</p>
    </div>
    <!-- <el-button type="sucess" @click="ce">测</el-button> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
    };
  },
  methods: {
    ce(){
      alert(this.info.tianqi == "雨");
    }
  },
  computed: {
    weatherBackgroundClass(){ 
      if (this.info.tianqi == "雷") {
        return "color-storm";
      } else if (this.info.tianqi == "雨") {
        return "color-rain";
      } else if (this.info.tianqi == "雪") {
        return "color-snow";
      } else {
        console.log(this.info.night);
        if (this.info.night) {
         return "color-moon";
        } else {
          return "color-sunny";
        }
      }},
    weatherClass(){
      if (this.info.tianqi == "雷") {
        return "storm";
      } else if (this.info.tianqi == "雨") {
        return  "rain";
      } else if (this.info.tianqi == "雪") {
        return  "snow";
      } else {
        console.log(this.info.night);
        if (this.info.night) {
          return  "moon";
        } else {
          return  "sunny";
        }
      }},
  },
  props: ["info"]
};
</script>

<style>
.card {
  width: 220px;
  background-color: #3c3b3d;
  float: left;
  margin: 0 20px 20px 0;
  overflow: hidden;
}

.card:nth-child(5n) {
  margin-right: 0;
}
.card-color {
  position: relative;
  width: 100%;
  padding: 6.5em 1em;
  display: block;
}

.card-color:after {
  position: absolute;
  content: "";
  top: 0;
  right: 0;
  height: 100%;
  width: 50%;
}

.card-color.color-sunny {
  background-color: #4fc1e9;
}

.card-color.color-snow {
  background-color: #ccd1d9;
}

.card-color.color-moon {
  background-color: #000;
}

.card-color.color-storm {
  background-color: #656d78;
}

.card-color.color-rain {
  background-color: #41ba9c;
}

.card-info {
  padding: 1em;
  color: #808080;
  text-align: center;
}

.card-info p {
  font-size: 0.85rem;
  margin-bottom: 0.75em;
}

.card-info p:first-child {
  font-weight: 600;
  font-size: 0.9rem;
  text-transform: uppercase;
  color: #fff;
}

.card-info p:last-child {
  margin-bottom: 0;
}

/* Sunny */

.sunny {
  animation: sunny 9s linear infinite;
  -webkit-animation: sunny 9s linear infinite;
  background: #ffe400;
  border-radius: 100%;
  box-shadow: rgba(255, 255, 0, 0.1) 0 0 5px 5px;
  content: "";
  height: 90px;
  width: 90px;
  position: absolute;
  left: 60px;
  top: 60px;
}

.sunny:before {
  animation: sunglow 9s ease-in-out infinite;
  -webkit-animation: sunglow 9s ease-in-out infinite;
  background: #ffee44;
  box-shadow: rgba(255, 255, 0, 1) 0 0 5px 1px;
  border-radius: 100%;
  content: "";
  height: 86px;
  width: 86px;
  position: absolute;
  left: 2px;
  top: 2px;
}

.sunny:after {
  animation: sunshadow 9s ease-in-out infinite;
  -webkit-animation: sunshadow 9s ease-in-out infinite;
  background: #000000;
  border-radius: 50%;
  content: "";
  height: 15px;
  width: 120px;
  opacity: 0.2;
  position: absolute;
  left: -15px;
  bottom: -40px;
  transform: scale(0.7);
  -webkit-transform: scale(0.7);
}

@keyframes sunny {
  50% {
    transform: translateY(-20px);
    -webkit-transform: translateY(-20px);
    box-shadow: rgba(255, 255, 0, 0.2) 0 0 5px 15px;
  }
}

@-webkit-keyframes sunny {
  50% {
    transform: translateY(-20px);
    -webkit-transform: translateY(-20px);
    box-shadow: rgba(255, 255, 0, 0.2) 0 0 5px 15px;
  }
}

@keyframes sunglow {
  50% {
    box-shadow: rgba(255, 255, 0, 0.1) 0 0 5px 10px;
  }
}

@-webkit-keyframes sunglow {
  50% {
    box-shadow: rgba(255, 255, 0, 0.1) 0 0 5px 10px;
  }
}

@keyframes sunshadow {
  50% {
    transform: translateY(20px) scale(1);
    -webkit-transform: translateY(20px) scale(1);
    opacity: 0.05;
  }
}

@-webkit-keyframes sunshadow {
  50% {
    transform: translateY(20px) scale(1);
    -webkit-transform: translateY(20px) scale(1);
    opacity: 0.05;
  }
}

/* Moon */

.moon {
  animation: moon_star 5s ease-in-out infinite;
  -webkit-animation: moon_star 5s ease-in-out infinite;
  background-color: #fff;
  border-radius: 50%;
  box-shadow: #ffffff 26px 7px 0 -1px,
    rgba(255, 255, 255, 0.1) -36px -19px 0 -1px,
    rgba(255, 255, 255, 0.1) -51px -34px 0 -1px, #ffffff -52px -62px 0 -1px,
    #ffffff 14px -37px, rgba(255, 255, 255, 0.1) 41px -19px, #ffffff 34px -50px,
    rgba(255, 255, 255, 0.1) 14px -71px 0 -1px, #ffffff 64px -21px 0 -1px,
    rgba(255, 255, 255, 0.1) 32px -85px 0 -1px, #ffffff 64px -90px,
    rgba(255, 255, 255, 0.1) 60px -67px 0 -1px, #ffffff 34px -127px,
    rgba(255, 255, 255, 0.1) -26px -103px 0 -1px;
  height: 4px;
  width: 4px;
  opacity: 1;
  position: absolute;
  left: 90px;
  top: 155px;
}

.moon:before {
  animation: moon 9s ease-in-out infinite;
  -webkit-animation: moon 9s ease-in-out infinite;
  border-radius: 50%;
  box-shadow: #ffffff -35px 0;
  content: "";
  height: 100px;
  width: 100px;
  position: absolute;
  top: -106px;
  -webkit-transform: rotate(-5deg);
  -webkit-transform-origin: 0 50%;
}

.moon:after {
  animation: moon 9s ease-in-out infinite;
  -webkit-animation: moon 9s ease-in-out infinite;
  border-radius: 50%;
  box-shadow: rgba(0, 0, 0, 0.2) -5px 0 0;
  content: "";
  height: 100px;
  width: 100px;
  position: absolute;
  top: -106px;
  left: -30px;
  transform: rotate(-5deg);
  -webkit-transform: rotate(-5deg);
  transform-origin: 30px 50%;
  -webkit-transform-origin: 30px 50%;
}

@keyframes moon {
  50% {
    transform: rotate(10deg);
    -webkit-transform: rotate(10deg);
  }
}

@-webkit-keyframes moon {
  50% {
    transform: rotate(10deg);
    -webkit-transform: rotate(10deg);
  }
}

@keyframes moon_star {
  50% {
    box-shadow: rgba(255, 255, 255, 0.1) 26px 7px 0 -1px,
      #ffffff -36px -19px 0 -1px, #ffffff -51px -34px 0 -1px,
      rgba(255, 255, 255, 0.1) -52px -62px 0 -1px,
      rgba(255, 255, 255, 0.1) 14px -37px, #ffffff 41px -19px,
      rgba(255, 255, 255, 0.1) 34px -50px, #ffffff 14px -71px 0 -1px,
      rgba(255, 255, 255, 0.1) 64px -21px 0 -1px, #ffffff 32px -85px 0 -1px,
      rgba(255, 255, 255, 0.1) 64px -90px, #ffffff 60px -67px 0 -1px,
      rgba(255, 255, 255, 0.1) 34px -127px, #ffffff -26px -103px 0 -1px;
  }
}

@-webkit-keyframes moon_star {
  50% {
    box-shadow: rgba(255, 255, 255, 0.1) 26px 7px 0 -1px,
      #ffffff -36px -19px 0 -1px, #ffffff -51px -34px 0 -1px,
      rgba(255, 255, 255, 0.1) -52px -62px 0 -1px,
      rgba(255, 255, 255, 0.1) 14px -37px, #ffffff 41px -19px,
      rgba(255, 255, 255, 0.1) 34px -50px, #ffffff 14px -71px 0 -1px,
      rgba(255, 255, 255, 0.1) 64px -21px 0 -1px, #ffffff 32px -85px 0 -1px,
      rgba(255, 255, 255, 0.1) 64px -90px, #ffffff 60px -67px 0 -1px,
      rgba(255, 255, 255, 0.1) 34px -127px, #ffffff -26px -103px 0 -1px;
  }
}

/* storm */

.storm {
  animation: storm 9s ease-in-out infinite;
  -webkit-animation: storm 9s ease-in-out infinite;
  background: #393939;
  border-radius: 50%;
  box-shadow: #393939 65px -25px 0 -5px, #393939 25px -25px,
    #393939 5px 0px 0 2px, #393939 10px 0px 0 2px, #393939 15px 0px 0 2px,
    #393939 20px 0px 0 2px, #393939 25px 0px 0 2px, #393939 30px 0px 0 2px,
    #393939 35px 0px 0 2px, #393939 40px 0px 0 2px, #393939 45px 0px 0 2px,
    #393939 50px 0px 0 2px, #393939 55px 0px 0 2px, #393939 60px 0px 0 2px,
    #393939 65px 0px 0 2px, #393939 70px 0px 0 2px, #393939 75px 0px 0 2px;
  height: 50px;
  width: 50px;
  position: absolute;
  left: 40px;
  top: 80px;
}

.storm:after {
  animation: storm_shadow 9s ease-in-out infinite;
  -webkit-animation: storm_shadow 9s ease-in-out infinite;
  background: #000;
  border-radius: 50%;
  content: "";
  height: 15px;
  width: 120px;
  opacity: 0.2;
  position: absolute;
  left: 5px;
  bottom: -60px;
  transform: scale(0.7);
  -webkit-transform: scale(0.7);
}

.storm:before {
  animation: storm_thunder 3s steps(1, end) infinite;
  -webkit-animation: storm_thunder 3s steps(1, end) infinite;
  border-right: 7px solid transparent;
  border-top: 33px solid yellow;
  box-shadow: yellow -2px -30px, rgba(255, 258, 0, 0.4) -2px -30px 10px;
  content: "";
  display: block;
  height: 0;
  width: 0;
  position: absolute;
  left: 57px;
  top: 70px;
  transform: rotate(14deg);
  -webkit-transform: rotate(14deg);
  transform-origin: 50% -60px;
  -webkit-transform-origin: 50% -60px;
}

@keyframes storm {
  50% {
    transform: translateY(-20px);
  }
}

@-webkit-keyframes storm {
  50% {
    -webkit-transform: translateY(-20px);
  }
}

@keyframes storm_shadow {
  50% {
    transform: translateY(20px) scale(1);
    opacity: 0.05;
  }
}

@-webkit-keyframes storm_shadow {
  50% {
    -webkit-transform: translateY(20px) scale(1);
    opacity: 0.05;
  }
}

@keyframes storm_thunder {
  0% {
    transform: rotate(20deg);
    opacity: 1;
  }
  5% {
    transform: rotate(-34deg);
    opacity: 1;
  }
  10% {
    transform: rotate(0deg);
    opacity: 1;
  }
  15% {
    transform: rotate(-34deg);
    opacity: 0;
  }
}

@-webkit-keyframes storm_thunder {
  0% {
    transform: rotate(20deg);
    -webkit-transform: rotate(20deg);
    opacity: 1;
  }
  5% {
    transform: rotate(-34deg);
    -webkit-transform: rotate(-34deg);
    opacity: 1;
  }
  10% {
    transform: rotate(0deg);
    -webkit-transform: rotate(0deg);
    opacity: 1;
  }
  15% {
    transform: rotate(-34deg);
    -webkit-transform: rotate(-34deg);
    opacity: 0;
  }
}

/* snow */

.snow {
  animation: snow 9s ease-in-out infinite 1s;
  -webkit-animation: snow 9s ease-in-out infinite 1s;
  background: #ffffff;
  border-radius: 50%;
  box-shadow: #ffffff 65px -25px 0 -5px, #ffffff 25px -25px,
    #ffffff 5px 0px 0 2px, #ffffff 10px 0px 0 2px, #ffffff 15px 0px 0 2px,
    #ffffff 20px 0px 0 2px, #ffffff 25px 0px 0 2px, #ffffff 30px 0px 0 2px,
    #ffffff 35px 0px 0 2px, #ffffff 40px 0px 0 2px, #ffffff 45px 0px 0 2px,
    #ffffff 50px 0px 0 2px, #ffffff 55px 0px 0 2px, #ffffff 60px 0px 0 2px,
    #ffffff 65px 0px 0 2px, #ffffff 70px 0px 0 2px, #ffffff 75px 0px 0 2px;
  display: block;
  height: 50px;
  width: 50px;
  position: absolute;
  left: 40px;
  top: 80px;
}

.snow:after {
  animation: snow_shadow 9s ease-in-out infinite 1s;
  -webkit-animation: snow_shadow 9s ease-in-out infinite 1s;
  background: #000000;
  border-radius: 50%;
  content: "";
  height: 15px;
  width: 120px;
  opacity: 0.2;
  position: absolute;
  left: 8px;
  bottom: -60px;
  transform: scale(0.7);
  -webkit-transform: scale(0.7);
}

.snow:before {
  animation: snow_snow 2s infinite linear;
  -webkit-animation: snow_snow 2s infinite linear;
  content: "";
  border-radius: 50%;
  display: block;
  height: 7px;
  width: 7px;
  opacity: 0.8;
  transform: scale(0.9);
  -webkit-transform: scale(0.9);
}

@keyframes snow {
  50% {
    transform: translateY(-20px);
  }
}

@-webkit-keyframes snow {
  50% {
    -webkit-transform: translateY(-20px);
  }
}

@keyframes snow_shadow {
  50% {
    transform: translateY(20px) scale(1);
    opacity: 0.05;
  }
}

@-webkit-keyframes snow_shadow {
  50% {
    -webkit-transform: translateY(20px) scale(1);
    opacity: 0.05;
  }
}

@keyframes snow_snow {
  0% {
    box-shadow: rgba(238, 238, 238, 0) 30px 30px,
      rgba(238, 238, 238, 0) 40px 40px, #eeeeee 50px 75px, #eeeeee 55px 50px,
      #eeeeee 70px 100px, #eeeeee 80px 95px, #eeeeee 110px 45px,
      #eeeeee 90px 35px;
  }
  25% {
    box-shadow: #eeeeee 30px 45px, #eeeeee 40px 60px, #eeeeee 50px 90px,
      #eeeeee 55px 65px, rgba(238, 238, 238, 0) 70px 120px,
      rgba(238, 238, 238, 0) 80px 120px, #eeeeee 110px 70px, #eeeeee 90px 60px;
  }
  26% {
    box-shadow: #eeeeee 30px 45px, #eeeeee 40px 60px, #eeeeee 50px 90px,
      #eeeeee 55px 65px, rgba(238, 238, 238, 0) 70px 40px,
      rgba(238, 238, 238, 0) 80px 20px, #eeeeee 110px 70px, #eeeeee 90px 60px;
  }
  50% {
    box-shadow: #eeeeee 30px 70px, #eeeeee 40px 80px,
      rgba(238, 238, 238, 0) 50px 100px, #eeeeee 55px 80px, #eeeeee 70px 60px,
      #eeeeee 80px 45px, #eeeeee 110px 95px, #eeeeee 90px 85px;
  }
  51% {
    box-shadow: #eeeeee 30px 70px, #eeeeee 40px 80px,
      rgba(238, 238, 238, 0) 50px 45px, #eeeeee 55px 80px, #eeeeee 70px 60px,
      #eeeeee 80px 45px, #eeeeee 110px 95px, #eeeeee 90px 85px;
  }
  75% {
    box-shadow: #eeeeee 30px 95px, #eeeeee 40px 100px, #eeeeee 50px 60px,
      rgba(238, 238, 238, 0) 55px 95px, #eeeeee 70px 80px, #eeeeee 80px 70px,
      rgba(238, 238, 238, 0) 110px 120px, rgba(238, 238, 238, 0) 90px 110px;
  }
  76% {
    box-shadow: #eeeeee 30px 95px, #eeeeee 40px 100px, #eeeeee 50px 60px,
      rgba(238, 238, 238, 0) 55px 35px, #eeeeee 70px 80px, #eeeeee 80px 70px,
      rgba(238, 238, 238, 0) 110px 25px, rgba(238, 238, 238, 0) 90px 15px;
  }
  100% {
    box-shadow: rgba(238, 238, 238, 0) 30px 120px,
      rgba(238, 238, 238, 0) 40px 120px, #eeeeee 50px 75px, #eeeeee 55px 50px,
      #eeeeee 70px 100px, #eeeeee 80px 95px, #eeeeee 110px 45px,
      #eeeeee 90px 35px;
  }
}

@-webkit-keyframes snow_snow {
  0% {
    box-shadow: rgba(238, 238, 238, 0) 30px 30px,
      rgba(238, 238, 238, 0) 40px 40px, #eeeeee 50px 75px, #eeeeee 55px 50px,
      #eeeeee 70px 100px, #eeeeee 80px 95px, #eeeeee 110px 45px,
      #eeeeee 90px 35px;
  }
  25% {
    box-shadow: #eeeeee 30px 45px, #eeeeee 40px 60px, #eeeeee 50px 90px,
      #eeeeee 55px 65px, rgba(238, 238, 238, 0) 70px 120px,
      rgba(238, 238, 238, 0) 80px 120px, #eeeeee 110px 70px, #eeeeee 90px 60px;
  }
  26% {
    box-shadow: #eeeeee 30px 45px, #eeeeee 40px 60px, #eeeeee 50px 90px,
      #eeeeee 55px 65px, rgba(238, 238, 238, 0) 70px 40px,
      rgba(238, 238, 238, 0) 80px 20px, #eeeeee 110px 70px, #eeeeee 90px 60px;
  }
  50% {
    box-shadow: #eeeeee 30px 70px, #eeeeee 40px 80px,
      rgba(238, 238, 238, 0) 50px 100px, #eeeeee 55px 80px, #eeeeee 70px 60px,
      #eeeeee 80px 45px, #eeeeee 110px 95px, #eeeeee 90px 85px;
  }
  51% {
    box-shadow: #eeeeee 30px 70px, #eeeeee 40px 80px,
      rgba(238, 238, 238, 0) 50px 45px, #eeeeee 55px 80px, #eeeeee 70px 60px,
      #eeeeee 80px 45px, #eeeeee 110px 95px, #eeeeee 90px 85px;
  }
  75% {
    box-shadow: #eeeeee 30px 95px, #eeeeee 40px 100px, #eeeeee 50px 60px,
      rgba(238, 238, 238, 0) 55px 95px, #eeeeee 70px 80px, #eeeeee 80px 70px,
      rgba(238, 238, 238, 0) 110px 120px, rgba(238, 238, 238, 0) 90px 110px;
  }
  76% {
    box-shadow: #eeeeee 30px 95px, #eeeeee 40px 100px, #eeeeee 50px 60px,
      rgba(238, 238, 238, 0) 55px 35px, #eeeeee 70px 80px, #eeeeee 80px 70px,
      rgba(238, 238, 238, 0) 110px 25px, rgba(238, 238, 238, 0) 90px 15px;
  }
  100% {
    box-shadow: rgba(238, 238, 238, 0) 30px 120px,
      rgba(238, 238, 238, 0) 40px 120px, #eeeeee 50px 75px, #eeeeee 55px 50px,
      #eeeeee 70px 100px, #eeeeee 80px 95px, #eeeeee 110px 45px,
      #eeeeee 90px 35px;
  }
}

/*Rain*/

.rain {
  animation: rain 9s ease-in-out infinite 1s;
  -webkit-animation: rain 9s ease-in-out infinite 1s;
  background: #cccccc;
  border-radius: 50%;
  box-shadow: #cccccc 65px -25px 0 -5px, #cccccc 25px -25px,
    #cccccc 5px 0px 0 2px, #cccccc 10px 0px 0 2px, #cccccc 15px 0px 0 2px,
    #cccccc 20px 0px 0 2px, #cccccc 25px 0px 0 2px, #cccccc 30px 0px 0 2px,
    #cccccc 35px 0px 0 2px, #cccccc 40px 0px 0 2px, #cccccc 45px 0px 0 2px,
    #cccccc 50px 0px 0 2px, #cccccc 55px 0px 0 2px, #cccccc 60px 0px 0 2px,
    #cccccc 65px 0px 0 2px, #cccccc 70px 0px 0 2px, #cccccc 75px 0px 0 2px;
  display: block;
  height: 50px;
  width: 50px;
  position: absolute;
  left: 40px;
  top: 80px;
}

.rain:after {
  animation: rain_shadow 9s ease-in-out infinite 1s;
  -webkit-animation: rain_shadow 9s ease-in-out infinite 1s;
  background: #000000;
  border-radius: 50%;
  content: "";
  height: 15px;
  width: 120px;
  opacity: 0.2;
  position: absolute;
  left: 5px;
  bottom: -60px;
  transform: scale(0.7);
  -webkit-transform: scale(0.7);
}

.rain:before {
  animation: rain_rain 0.7s infinite linear;
  -webkit-animation: rain_rain 0.7s infinite linear;
  content: "";
  background: transparent;
  margin-left: 0px;
  border-radius: 50%;
  display: block;
  height: 6px;
  width: 3px;
  opacity: 0.3;
  transform: scale(0.9);
  -webkit-transform: scale(0.9);
}

@keyframes rain {
  50% {
    transform: translateY(-20px);
  }
}

@-webkit-keyframes rain {
  50% {
    -webkit-transform: translateY(-20px);
  }
}

@keyframes rain_shadow {
  50% {
    transform: translateY(20px) scale(1);
    opacity: 0.05;
  }
}

@-webkit-keyframes rain_shadow {
  50% {
    transform: translateY(20px) scale(1);
    -webkit-transform: translateY(20px) scale(1);
    opacity: 0.05;
  }
}

@keyframes rain_rain {
  0% {
    box-shadow: rgba(0, 0, 0, 0) 30px 30px, rgba(0, 0, 0, 0) 40px 40px,
      blue 50px 75px, blue 55px 50px, blue 70px 100px, blue 80px 95px,
      blue 110px 45px, blue 90px 35px;
  }
  25% {
    box-shadow: blue 30px 45px, blue 40px 60px, blue 50px 90px, blue 55px 65px,
      rgba(0, 0, 0, 0) 70px 120px, rgba(0, 0, 0, 0) 80px 120px, blue 110px 70px,
      blue 90px 60px;
  }
  26% {
    box-shadow: blue 30px 45px, blue 40px 60px, blue 50px 90px, blue 55px 65px,
      rgba(0, 0, 0, 0) 70px 40px, rgba(0, 0, 0, 0) 80px 20px, blue 110px 70px,
      blue 90px 60px;
  }
  50% {
    box-shadow: blue 30px 70px, blue 40px 80px, rgba(0, 0, 0, 0) 50px 100px,
      blue 55px 80px, blue 70px 60px, blue 80px 45px, blue 110px 95px,
      blue 90px 85px;
  }
  51% {
    box-shadow: blue 30px 70px, blue 40px 80px, rgba(0, 0, 0, 0) 50px 45px,
      blue 55px 80px, blue 70px 60px, blue 80px 45px, blue 110px 95px,
      blue 90px 85px;
  }
  75% {
    box-shadow: blue 30px 95px, blue 40px 100px, blue 50px 60px,
      rgba(0, 0, 0, 0) 55px 95px, blue 70px 80px, blue 80px 70px,
      rgba(0, 0, 0, 0) 110px 120px, rgba(0, 0, 0, 0) 90px 110px;
  }
  76% {
    box-shadow: blue 30px 95px, blue 40px 100px, blue 50px 60px,
      rgba(0, 0, 0, 0) 55px 35px, blue 70px 80px, blue 80px 70px,
      rgba(0, 0, 0, 0) 110px 25px, rgba(0, 0, 0, 0) 90px 15px;
  }
  100% {
    box-shadow: rgba(0, 0, 0, 0) 30px 120px, rgba(0, 0, 0, 0) 40px 120px,
      blue 50px 75px, blue 55px 50px, blue 70px 100px, blue 80px 95px,
      blue 110px 45px, blue 90px 35px;
  }
}

@-webkit-keyframes rain_rain {
  0% {
    box-shadow: rgba(0, 0, 0, 0) 30px 30px, rgba(0, 0, 0, 0) 40px 40px,
      blue 50px 75px, blue 55px 50px, blue 70px 100px, blue 80px 95px,
      blue 110px 45px, blue 90px 35px;
  }
  25% {
    box-shadow: blue 30px 45px, blue 40px 60px, blue 50px 90px, blue 55px 65px,
      rgba(0, 0, 0, 0) 70px 120px, rgba(0, 0, 0, 0) 80px 120px, blue 110px 70px,
      blue 90px 60px;
  }
  26% {
    box-shadow: blue 30px 45px, blue 40px 60px, blue 50px 90px, blue 55px 65px,
      rgba(0, 0, 0, 0) 70px 40px, rgba(0, 0, 0, 0) 80px 20px, blue 110px 70px,
      blue 90px 60px;
  }
  50% {
    box-shadow: blue 30px 70px, blue 40px 80px, rgba(0, 0, 0, 0) 50px 100px,
      blue 55px 80px, blue 70px 60px, blue 80px 45px, blue 110px 95px,
      blue 90px 85px;
  }
  51% {
    box-shadow: blue 30px 70px, blue 40px 80px, rgba(0, 0, 0, 0) 50px 45px,
      blue 55px 80px, blue 70px 60px, blue 80px 45px, blue 110px 95px,
      blue 90px 85px;
  }
  75% {
    box-shadow: blue 30px 95px, blue 40px 100px, blue 50px 60px,
      rgba(0, 0, 0, 0) 55px 95px, blue 70px 80px, blue 80px 70px,
      rgba(0, 0, 0, 0) 110px 120px, rgba(0, 0, 0, 0) 90px 110px;
  }
  76% {
    box-shadow: blue 30px 95px, blue 40px 100px, blue 50px 60px,
      rgba(0, 0, 0, 0) 55px 35px, blue 70px 80px, blue 80px 70px,
      rgba(0, 0, 0, 0) 110px 25px, rgba(0, 0, 0, 0) 90px 15px;
  }
  100% {
    box-shadow: rgba(0, 0, 0, 0) 30px 120px, rgba(0, 0, 0, 0) 40px 120px,
      blue 50px 75px, blue 55px 50px, blue 70px 100px, blue 80px 95px,
      blue 110px 45px, blue 90px 35px;
  }
}
</style>
