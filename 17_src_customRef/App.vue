<template>
  <input type="text" v-model="keyWord" />
  <h3>{{ keyWord }}</h3>
</template>

<script>
import { ref, customRef } from "vue";
export default {
  name: "App",
  setup() {
    //自定義ref --- 名為myRef
    function myRef(value, delay) {
      let timer;
      return customRef((track, trigger) => {
        return {
          get() {
            console.log(`有人從myRef這個容器中讀取數據了, 我把${value}給他了`);
            track(); //通知vue追蹤value的變化 (提前跟get商量一下, 讓他認為這個value是有用的)
            return value;
          },
          set(newValue) {
            console.log(`有人從myRef這個容器中修改數據了 改為: ${newValue}`);
            clearTimeout(timer);
            timer = setTimeout(() => {
              value = newValue;
              trigger(); //通知vue重新解析模板
            }, delay);
          },
        };
      });
    }
    // let keyWord = ref("helo"); //使用Vue提供的ref
    let keyWord = myRef("hello", 500);
    return { keyWord };
  },
};
</script>
