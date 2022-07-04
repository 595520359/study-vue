<script>
export default {
  data() {
    return {
      age: 18,
      isShow1: true,
      isShow2: true,
      sex: 'man',
    }
  },
  watch: {},
  methods: {},
  computed: {},
}
</script>

<template>
  <div>
    <!-- v-if test -->
    <p v-if="age > 18" class="up18">我是成年人</p>
    <p v-else-if="age === 18" class="the18">我刚满18岁</p>
    <p v-else class="down18">我是小朋友</p>
    <button @click="age = 13">到13岁|{{ age }}</button>
    <button @click="age = 18">到18岁|{{ age }}</button>
    <button @click="age = 24">到24岁|{{ age }}</button>
    <br />
    <button @click="isShow1 = !isShow1">改变isShow1|{{ isShow1 }}</button>
    <template v-if="isShow1">
      <p>展示1</p>
      <p>展示2</p>
      <p>展示3</p>
      <p>展示4</p>
    </template>
    <!-- v-show -->
    <p v-show="sex === 'man'">男生</p>
    <p v-show="sex === 'woman'">女生</p>
    <button @click="sex = 'man'">到男生|{{ sex }}</button>
    <button @click="sex = 'woman'">到女生|{{ sex }}</button>
    <!-- 
      v-if 是“真实的”按条件渲染，因为它确保了条件区块内的事件监听器和子组件都会在切换时被销毁与重建。

      v-if 也是懒加载的：如果在初次渲染时条件值为 false，则不会做任何事。条件区块会直到条件首次变为 true 时才渲染。

      相比之下，v-show 简单许多，元素无论初始条件如何，始终会被渲染，仅作 CSS class 的切换。

      总的来说，v-if 在首次渲染时的切换成本比 v-show 更高。因此当你需要非常频繁切换时 v-show 会更好，而运行时不常改变的时候 v-if 会更合适。
     -->
    <br />
    <button @click="isShow2 = !isShow2">改变isShow2|{{ isShow2 }}</button>
    <h2 v-if="isShow2">v-if</h2>
    <h2 v-show="!isShow2">v-show</h2>
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

.up18 {
  background-color: rgb(255, 0, 0);
}

.the18 {
  background-color: rgb(255, 255, 0);
}

.down18 {
  background-color: rgb(0, 255, 0);
}
</style>
