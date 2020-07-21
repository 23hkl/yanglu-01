<template>
  <div id="choiceness">
    <div>
       <p class="">精选专题</p>
       <i class="van-icon van-icon-arrow"></i>
    </div>
    <div class="isc">
      <van-loading v-if="loading" /> 
      <ul v-else>
          <Ztitle v-for="item in list" :d = "item" :key="item.id"  />
    
      </ul>
    </div>
  </div>
</template>

<script>
// 引入Ztitle通过下面的this.http.get获取接口，将数据载入到Ztitle.vue
import Ztitle from "./Ztitle"
export default {
  components: {
      Ztitle
  },
  props: {},
  data() {
    return {
        list:[],
        loading:true
    }
  },
  watch: {},
  computed: {},
  methods: {},
  created() {
      //  创建内容
      // this.http.get发送请求
      // then()方法是异步执行，执行完then前面的才能执行then后面的，避免了数据没获取到的问题
      this.http.get("https://api.it120.cc/small4/cms/news/list").then((msg)=>{
             console.log(msg)
             this.list = msg.data.data
             this.loading = false
      })
  },
  mounted() {}
}
</script>
<style lang="less">
#choiceness {
  width: 100%;
  height: 4.42rem;
  border-bottom: 0.14rem solid #f5f5f5;
  > div:nth-of-type(1) {
    font-size: 0.22rem;
    display: flex;
    justify-content: space-between;
    padding: 0 2rem;
    align-items: center;
    text-align: center;
    height: 0.65rem;
    // border-bottom: 0.01rem solid #E9E9E9;
    > i {
      font-size: 0.2rem;
    }
  }
  > div:nth-of-type(2) {
    width: 100%;
    height: 3.78rem;
    // overflow: hidden;
    overflow: auto;
    > ul {
      width: 22.7rem;
      display: flex;
      > li {
        width: 4.42rem;
        height: 2.84rem;
        margin-left: 0.12rem;
        > img {
          width: 4.42rem;
          height: 2.84rem;
          display: block;
          border-radius: 0.06rem;
        }
        > p:nth-of-type(1) {
          font-size: 0.18rem;
          color: #2c2c2c;
          margin-top: 0.12rem;
          width: 4rem;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
        }
        > p:nth-of-type(2) {
          font-size: 0.14rem;
          color: #a8a8a8;
          margin-top: 0.2rem;
          width: 3.24rem;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
        }
      }
    }
  }
}
</style>