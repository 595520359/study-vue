<script>
export default {
  data() {
    return {
      parentMessage: 'Parent',
      items: [
        {
          // id: 3,
          message: 'Foo',
          children: ['F1', 'F2'],
        },
        {
          // id: 2,
          message: 'Bar',
          children: ['B1', 'B2', 'B3'],
        },
      ],
      test_array: [1, 'two'],
      myObject: {
        title: 'How to do lists in Vue',
        author: 'Jane Doe',
        publishedAt: '2016-04-10',
      },
    }
  },
  watch: {},
  methods: {},
  computed: {},
}
</script>

<template>
  <div>
    <!-- 循环数组 -->
    <ul>
      <li v-for="item in test_array">
        {{ item }}
      </li>
    </ul>
    <!-- 循环字典中带有序号 -->
    <ul>
      <li v-for="(item, index) in items">
        {{ parentMessage }} - {{ index }} - {{ item.message }}
      </li>
    </ul>
    <!-- 多层嵌套循环 -->
    <ul>
      <li v-for="item in items">
        <span
          :id="item.message + (index + 1)"
          v-for="(childItem, index) in item.children"
        >
          {{ item.message }} --- {{ childItem }}
          <br v-if="item.children.length != index + 1" />
        </span>
      </li>
    </ul>
    <!-- 循环对象 -->
    <ul>
      <li v-for="(value, key, index) in myObject">
        {{ key }}: {{ value }} --- {{ index }}
      </li>
    </ul>
    <ul>
      <div v-for="item in items" :key="item.id">
        <li>{{ item }}</li>
      </div>
    </ul>
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
