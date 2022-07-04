<script>
export default {
  data() {
    return {
      message: 'helloworld',
      isActive: false,
      isActiveA: false,
      isActiveB: true,
      testWatch: true,
      pinkBackground: 'pink-background',
      bindObj: {
        id: 'one',
        class: 'red-color',
        style: {
          fontSize: '4rem',
          marginLeft: '2vw',
        },
      },
      watchObj: {
        name: '张三',
        age: 26,
        sex: '男',
        isLog: true,
      },
    }
  },
  watch: {
    // testWatch(newV, oldV) {
    //   if (newV) {
    //     this.isActive = true
    //   }
    // watchObj(newv, oldv) {
    //   console.log('change!!!')
    // },
    // watchObj: {
    //   handler(newv, oldv) {
    //     console.log('change!!!')
    //   },
    //   deep: true,
    // },
    'watchObj.isLog'(newv, oldv) {
      console.log('change!!!')
    },
  },
  methods: {},
  computed: {
    comIsActive() {
      return this.isActiveA && this.isActiveB
    },
  },
}
</script>

<template>
  <div>
    <!-- 通过对象绑定 -->
    <p v-bind="bindObj" :class="{ [pinkBackground]: isActive }">
      {{ message }}
    </p>
    <button @click="isActive = !isActive">改变</button>
    <!-- 通过计算属性控制 -->
    <p :class="{ [pinkBackground]: comIsActive }">
      {{ message }}
    </p>
    <button @click="isActiveA = !isActiveA">改变A|{{ isActiveA }}</button>
    <button @click="isActiveB = !isActiveB">改变B|{{ isActiveB }}</button>
    <br />
    <!-- 侦听器 -->
    <button @click="testWatch = !testWatch">
      改变侦听对象isLog|{{ testWatch }}
    </button>
    <br />
    <button @click="watchObj.isLog = !watchObj.isLog">
      改变侦听对象isLog|{{ watchObj.isLog }}
    </button>
  </div>
</template>

<style>
@import './assets/base.css';

body {
  margin-left: 2vw;
  font-size: 1.5rem;
}

.red-color {
  color: red;
}

.pink-background {
  background-color: pink;
}
</style>
