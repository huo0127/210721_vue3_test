<template>
  <div class="app">
    <h3>我是App組件</h3>
    <Suspense>
      <template v-slot:default>
        <Child />
      </template>
      <template v-slot:fallback>
        <h3>等等, 加載中...</h3>
      </template>
    </Suspense>
  </div>
</template>

<script>
// import Child from "./components/Child"; //靜態引入
import { defineAsyncComponent } from "vue";
//動態引入
const Child = defineAsyncComponent(() => import("./components/Child"));
export default {
  name: "App",
  components: { Child },
};
</script>

<style>
.app {
  background-color: gray;
  padding: 10px;
}
</style>
