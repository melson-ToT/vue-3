<template>
  <div @click="fn">点击这里</div>
</template>

<script>
import { useRouter,useRoute } from "vue.router";//引入路由
export default {
  setup() {

    //useRouter,useRoute 这两个函数，只能在 setup 的顶层执行

    //定义 router = 引入的路由
    const router = useRouter()

    //定义 router = 引入的路由信息
    const route = useRoute()

    //再将 router 代入到 fn的方法中
    const fn = () => {
      router.push("/home")
    };

    return {
      fn,
    };
  },
};
</script>

<style lang="less" scoped>
</style>