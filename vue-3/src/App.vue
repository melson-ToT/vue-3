<template>
  <p>依赖注入</p>
  <NameChild />
</template>
  
<script>

import NameChild from "./NameChild.vue"

import { ref, provide  } from "vue"

export default {
  setup() {
    const count = ref(10)

    //里面有两个阐述，参1：
    provide("count",count)

    return {
      count,
    }
  },

  components:{
    NameChild
  }
  

};
</script>

<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>