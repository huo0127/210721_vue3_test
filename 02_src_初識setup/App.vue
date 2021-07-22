<template>
  <h1>我是app組件</h1>
  <h2>姓名: {{ name }}</h2>
  <h2>年齡: {{ age }}</h2>
  <h3>性別: {{ gender }}</h3>
  <h3>a的值為: {{ number }}</h3>
  <button @click="sayHello">說話(vue2所配置的---sayHello)</button>
  <br />
  <br />
  <button @click="sayWelcome">說話(vue3所配置的---sayWelcome)</button>
  <br />
  <br />
  <button @click="test1">測試一下在vue2的配置中去讀取vue3的數據和方法</button>
  <br />
  <br />
  <button @click="test2">
    測試一下在vue3(setup)的配置中去讀取vue2的數據和方法
  </button>
</template>

<script>
// import { h } from "vue";
export default {
  name: "App",
  data() {
    return {
      gender: "male",
      // number: 100,
    };
  },
  methods: {
    sayWelcome() {
      alert("歡迎來到尚硅谷學習");
    },
    test1() {
      console.log(this.gender);
      console.log(this.name);
      console.log(this.age);
      console.log(this.sayHello);
    },
  },
  setup() {
    // 數據
    let name = "張三";
    let age = "18";
    let number = 200;

    //方法
    function sayHello() {
      alert(`我叫${name}, 今年${age}歲, 你好啊!!!`);
    }
    function test2() {
      console.log(name);
      console.log(age);
      console.log(sayHello);
      console.log(this.gender);
      console.log(this.welcome);
    }

    //返回一個對象(常用)
    return {
      name,
      age,
      sayHello,
      test2,
      number,
    };

    //返回一個函數(渲染函數)
    // return () => h("h1", "尚硅谷");
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
