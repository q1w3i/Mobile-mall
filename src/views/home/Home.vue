<template>
  <div>
    <div id="home">
      <nav-bar class="home-nav">
        <template v-slot:center> 
          <div>购物街</div>
        </template>
      </nav-bar>
     <home-swiper :banners="banners"></home-swiper>
     <recommend-view :recommends="recommends"></recommend-view>
    <feature-view/> 
    <tab-control class="tab-control" :titles="['流行','新款','精选']"
    @tabClick="tabClick"></tab-control>
    <goods-list :goods="showGoods"></goods-list>
    <ul>
      <li></li>
      <li></li>
      <li></li>
    </ul>
    </div>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
import TabControl from 'components/content/tabControl/TabControl'
import GoodsList from 'components/content/goods/GoodsList'


import HomeSwiper from './childComps/HomeSwiper'
import RecommendView from './childComps/RecommendView'
import FeatureView from './childComps/FeatureView'

import {getHomeMultidata,getHomeGoods} from 'network/home'

export default {
  name:"Home",
  components:{
    NavBar,
    HomeSwiper,
    RecommendView,
    FeatureView,
    TabControl,
    getHomeGoods,
    GoodsList
  },
  data(){
    return{
      banners:[],
      recommends:[],
      goods:{
        'pop':{page: 0,list:[]},
        'new':{page: 0,list:[]},
        'sell':{page: 0,list:[]},
      },
      currentType:'pop'
    }
  },
  computed:{
    showGoods() {
       return this.goods[this.currentType].list
    }
  },
  created(){
    this.getHomeMultidata()
    this.getHomeGoods('pop')
    this.getHomeGoods('new')
    this.getHomeGoods('sell')
  },
  methods:{
  // 事件监听相关代码
    tabClick(index) {
      switch(index){
        case 0:
          this.currentType='pop'
          break
        case 1:
          this.currentType='new'
          break
        case 2:
          this.currentType='sell'
          break
      }
    },

    // 网络请求相关代码
    getHomeMultidata(){
      getHomeMultidata().then(res=>{
      this.banners= res.data.banner.list;
      this.recommends = res.data.recommend.list;
    })
    },
    getHomeGoods(type){
      const page = this.goods[type].page+1
      getHomeGoods(type,page).then(res=>{
        this.goods[type].list.push(...res.data.list)
        this.goods[type].page += 1
    })
    }
  }


}
</script>

<style>
#home{
  padding-top: 44px;
}
.home-nav{
  background-color: var(--color-tint);
  color: #fff;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;
  z-index: 999;
}
.tab-control{
  position: sticky;
  top: 44px;
}
</style>