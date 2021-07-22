<template>
  <h2>我是test組件</h2>
  <h2>當前點擊的滑鼠座標為: x {{ point.x }} y {{ point.y }}</h2>
</template>

<script>
import usePoint from "../hooks/usePoint";
export default {
  name: "Test",
  setup() {
    let point = usePoint();
    return {
      point,
    };
  },
};
</script>
