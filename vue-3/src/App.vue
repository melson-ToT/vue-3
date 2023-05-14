<template>
  <p>{{ fathTime }} - <button @click="fb">暂停</button></p>
  <input type="text" v-model="value" />
  <button @click="fn">添加</button>
  <ul>
    <li v-for="item in list" :key="item.id">
      {{ item.name }} - <button @click="fa(item.id)">删除</button> 
    </li>
  </ul>
</template>

<script>
let dsq;
export default {
  data() {
    return {
      value: "",
      list: [
        {
          name: "zhangsan",
          id: 1,
        },
        {
          name: "lisi",
          id: 2,
        },
      ],
      timer: 0,
    };
  },

  mounted() {
    dsq = setInterval(()=>{
      this.timer = new Date().getTime();
    },1000)
  },

  computed: {
    fathTime() {
        let date = new Date(this.timer);
        let year = date.getFullYear();
        let month= date.getMonth() + 1;
        month= month< 10 ? ('0' + month) : month;
        let day = date.getDate();
        day = day < 10 ? ('0' + day ) : day ;
        let h = date.getHours();
        h = h < 10 ? ('0' + h) : h;
        let m = date.getMinutes();
        m = m < 10 ? ('0' + m) : m;
        let s = date.getSeconds();
        s = s < 10 ? ('0' + s) : s;
        return year + '-' + month + '-' + day + ' ' + h + ':' + m + ':' + s;
    },
  },

  methods: {
    fn() {
      this.list.push({
        id: new Date().getTime(),
        name: this.value,
      }),
        (this.value = "");
    },
    fa(id) {
      this.list = this.list.filter((item) => item.id != id);
    },
    fb(){
      clearInterval(dsq)
    }
  },
  
  beforeUnmount(){
    clearInterval(dsq)
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
