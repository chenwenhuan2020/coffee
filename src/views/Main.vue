<template>
  <div class="main">

    <!-- 二级路由 -->
    <div>
      <router-view></router-view>
    </div>

    <van-tabbar v-model="activeName" inactive-color="#646566" active-color="#f0134b" style="font-weight:bold" route>
      <van-tabbar-item :icon="item.icon" v-for="(item, index) in tabbarData" :key="index" :name="item.name" replace :to="item.path">
        <span>{{item.title}}</span>

        <!-- 具有插槽作用域的插槽 -->
        <template #icon="props">
          <img :src="props.active ? item.activeImg : item.inactiveImg" />
        </template>
        
      </van-tabbar-item>
    </van-tabbar>

  </div>
</template>

<script>
  export default {
    name: 'Main',
    data() {
      return {

        //激活标签的名称
        activeName: 'Home',

        tabbarData: [
          {
            title: '首页',
            icon: 'home-o',

            //标签名称、路由名称
            name: 'Home',

            path: '/main/home',

            inactiveImg: require('../assets/images/home.png'),
            activeImg: require('../assets/images/home1.png')
          },
          {
            title: '咖啡榜',
            icon: 'search',
            name: 'Menu',
            path: '/main/menu',
            inactiveImg: require('../assets/images/ka.png'),
            activeImg: require('../assets/images/ka1.png')
          },
          {
            title: '购物车',
            icon: 'friends-o',
            name: 'Shopbag',
            path: '/main/shopbag',
            inactiveImg: require('../assets/images/gou.png'),
            activeImg: require('../assets/images/gou1.png')
          },
          {
            title: '我的',
            icon: 'setting-o',
            name: 'My',
            path: '/main/my',
            inactiveImg: require('../assets/images/me.png'),
            activeImg: require('../assets/images/me1.png')
          }
        ]
      };
    },

    methods: {

    }
  }
</script>

<style lang="less" scoped>
  .main{
    padding-bottom: 50px;
  }
</style>