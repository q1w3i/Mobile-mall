<template>
      <tab-bar>
      <tab-bar-item path="/home" activeColor="#226DDD">
        <template v-slot:item-icon>
        <img src="~assets/img/tabbar/home.svg" alt="">
        </template>
        <template v-slot:item-icon-active>
        <img  src="~assets/img/tabbar/home_active.svg" alt="">
        </template>
        <template v-slot:item-text>
        <div>首页</div>
        </template>
      </tab-bar-item>
      <tab-bar-item path="/category" activeColor="#226DDD">
        <template v-slot:item-icon>
        <img slot="item-icon" src="~assets/img/tabbar/category.svg" alt="">
        </template>
        <template v-slot:item-icon-active>
        <img  src="~assets/img/tabbar/category_active.svg" alt="">
        </template>
        <template v-slot:item-text>
        <div >分类</div>
        </template>
      </tab-bar-item>
      <tab-bar-item path="/cart" activeColor="#226DDD">
        <template v-slot:item-icon>
        <img slot="item-icon" src="~assets/img/tabbar/cart.svg" alt="">
        </template>
        <template v-slot:item-icon-active>
        <img  src="~assets/img/tabbar\cart_active.svg" alt="">
        </template>
        <template v-slot:item-text>
        <div >购物车</div>
        </template>
      </tab-bar-item>
      <tab-bar-item path="/profile" activeColor="#226DDD">
        <template v-slot:item-icon>
        <img slot="item-icon" src="~assets/img/tabbar/profile.svg" alt="">
        </template>
        <template v-slot:item-icon-active>
        <img src="~assets/img/tabbar/profile_active.svg" alt="">
        </template>
        <template v-slot:item-text>
        <div>我的</div>
        </template>
      </tab-bar-item>
    </tab-bar>
</template>

<script>

import TabBar from 'common/tabbar/TabBar'
import TabBarItem from 'common/tabbar/TabBarItem'

export default {
  name:"MainTabBar",
  components: {
        TabBar, TabBarItem
      }
}
</script>

<style>

</style>