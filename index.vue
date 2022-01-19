
<!--
 * @Description:信号强度
 * @Author:lpeng3443002624@qq.com
 * @Date:2022-1-19 09:45:29
 * @LastEditors:lpeng3443002624@qq.com
 * @LastEditTime:2022-1-19 09:45:35
-->
<template>
  <div
    class="signal-strength"
    :style="{ transform: 'scale(' + _scaleX + ',' + _scaleY + ')' }"
  >
    <ul>
      <li
        v-for="i in 6"
        :key="i"
        :style="{
          background:
            '' + (i <= strength ? '#5cf548' : 'rgba(0, 0, 0, 0.4)') + ''
        }"
      ></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: `SignalStrength`,
  props: {
    //   尺寸
    width: {
      default: 60,
      validator: (value) => {
        console.log('_validator width', value)
        return (typeof value === 'number' && !isNaN(value)) || false
      }
    },
    height: {
      default: 40,
      validator: (value) => {
        console.log('_validator height', value)
        return (typeof value === 'number' && !isNaN(value)) || false
      }
    },
    // 信号强度，默认满格信号
    strength: {
      default: 6
    }
  },
  computed: {
    _scaleX () {
      return this.width / 60
    },
    _scaleY () {
      return this.height / 40
    }
  }
}
</script>

<style lang="less" scoped>
* {
  margin: 0;
  padding: 0;
  list-style: none;
}
.signal-strength {
  width: 60px;
  height: 40px;
}
ul {
  position: relative;
  width: 100%;
  height: 100%;
}
li {
  width: 5px;
  position: absolute;
  bottom: 0;
  border-radius: 10px;
  background: rgba(0, 0, 0, 0.5);
}
ul li:nth-child(1) {
  height: 10px;
  left: 0px;
}
ul li:nth-child(2) {
  height: 15px;
  left: 10px;
}
ul li:nth-child(3) {
  height: 20px;
  left: 20px;
}
ul li:nth-child(4) {
  height: 25px;
  left: 30px;
}
ul li:nth-child(5) {
  height: 30px;
  left: 40px;
}
ul li:nth-child(6) {
  height: 35px;
  left: 50px;
}
</style>
