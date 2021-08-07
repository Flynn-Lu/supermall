<template>
  <div id="home" class="wrapper">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners"/>
    <recommend-view :recommends="recommends"/>
  </div>
</template>

<script>
  
  import NavBar from 'components/common/navbar/NavBar'
  import {getHomeMultidata} from 'network/home'
  // import {Swiper, SwiperItem} from 'components/common/swiper'
import HomeSwiper from './childComps/HomeSwiper.vue'
import RecommendView from './childComps/RecommendView.vue'


  export default {
    name: "Home",
    components: {
        NavBar,

        HomeSwiper,
        RecommendView

    },
    data(){
      return { 
        // result:null
        banners:[],
        recommends:[]
        }
    },
    created(){
      getHomeMultidata().then(res=>{//异步操作
        console.log(res);
        // this.result=res;
        this.banners=res.data.banner.list;
        this.recommends=res.data.recommend.list;
      })
    }
  } 
</script>

<style scoped>
  
  .home-nav {
    background-color: var(--color-tint);
    color: #fff;

    
  }

  
</style>
