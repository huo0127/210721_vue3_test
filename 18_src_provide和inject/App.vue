<template>
  <div class="app">
    <h3>我是App組件(祖), {{ name }} --- {{ price }}</h3>
    <Child />
  </div>
</template>

<script>
import { provide, reactive, toRefs } from "vue";
import Child from "./components/Child";
export default {
  name: "App",
  components: { Child },
  setup() {
    let car = reactive({
      name: "mb",
      price: "40w",
    });
    provide("car", car); //給自己的後代組件傳遞數據
    return {
      ...toRefs(car),
    };
  },
};
</script>

<style>
.app {
  background-color: gray;
  padding: 10px;
}
</style>
