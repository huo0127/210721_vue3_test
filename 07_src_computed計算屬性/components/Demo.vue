<template>
  <h1>一個人的訊息</h1>
  姓: <input type="text" v-model="person.firstName" />
  <br />
  <br />
  名:<input type="text" v-model="person.lastName" />
  <br />
  <br />
  <span> 全名: {{ person.fullName }} </span>
  <br />
  <br />
  <span> 全名: <input type="text" v-model="person.fullName" /> </span>
  <br />
  <br />
</template>

<script>
import { reactive, computed } from "vue";
export default {
  name: "Demo",

  //數據
  setup() {
    let person = reactive({
      firstName: "張",
      lastName: "三",
    });

    //計算屬性---簡寫(沒有考慮計算屬性被修改的情況)
    // person.fullName = computed(() => {
    //   return person.firstName + "-" + person.lastName;
    // });

    //計算屬性---簡寫(考慮計算屬性被修改的情況)
    person.fullName = computed({
      get() {
        return person.firstName + "-" + person.lastName;
      },
      set(value) {
        const nameArr = value.split("-");
        person.firstName = nameArr[0];
        person.lastName = nameArr[1];
      },
    });

    //返回一個對象(常用)
    return {
      person,
    };
  },
};
</script>
