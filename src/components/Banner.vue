<template>
  <div class="yl-wrapper">
      <van-loading size="24px" v-if="loading" >加载中...</van-loading>
    <div v-else>
    <!-- 轮播图效果 -->
    <van-swipe class="yl-my-swipe" :autoplay="3000" indicator-color="white">
                <!-- 对默认为空数组banner循环 -->
                <van-swipe-item v-for="item of banners" :key="item.id">
                       <img :src="item.picUrl" alt="">
                </van-swipe-item>
    </van-swipe>
    <!-- 写入四个标签 -->
     <ul class="nav">
         <li class="">
             <img src="/static/cd1.7808faf.png" alt="">
             <p>签到</p>
         </li>
          <li class="">
             <img src="/static/cd1.7808faf.png" alt="">
            <p>礼券</p>
         </li>
          <li class="">
             <img src="/static/cd1.7808faf.png" alt="">
            <p>砍价</p>
         </li>
          <li class="">
             <img src="/static/cd1.7808faf.png" alt="">
            <p>专栏</p>
         </li>
     </ul>
     </div>
  </div>
</template>

<script>
export default {
  components:{},
  props:{},
  data(){
    return {
        // 默认数组为空
        banners:[],
        // 默认加载为加载
        loading:true
    }
  },
  watch:{},
  computed:{},
  methods:{},
     created(){
        //  创建内容
        // this.http.get发送请求
        // then()方法是异步执行，执行完then前面的才能执行then后面的，避免了数据没获取到的问题
            this.http.get("https://api.it120.cc/small4/banner/list").then((msg)=>{
                     
                  //   console.log(msg)
                     this.banners = msg.data.data
                     this.loading = false
            })
    },
  mounted(){}
}
</script>
<style lang="less" >
.yl-wrapper{
    position: relative;
    height: 414px;
    .nav{
    width: 100%;
    height: 1.4rem;
    background: white;
    position: absolute;
    left: 0;
    bottom: 0;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    -ms-flex-pack: distribute;
    justify-content: space-around;
    text-align: center;
    border-radius: 20% 20% 0 0;
    border-bottom: 0.2rem solid #F5F5F5;
    li{
        img{
            width: 0.58rem;
            height: 0.58rem;
            display: block;
            margin: 0 auto;
        }
    }
}
}
.yl-wrapper .nav li p{
        font-size: 0.26rem;
    margin-top: 0.17rem;
}
.yl-my-swipe{
    height: 414px;
    overflow: hidden;
}
.yl-my-swipe .van-swipe-item img{
    width:100%
}
</style>