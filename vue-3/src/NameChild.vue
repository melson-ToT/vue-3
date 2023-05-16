<template>
  <p>子组件--{{ num }}</p>
</template>

<script>
import { inject } from "vue"
export default {
  setup() {
    const num =  inject("count")
    return {
      num,
    };
  },
};
</script>
<style lang="less" scoped>
</style>