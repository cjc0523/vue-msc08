<template>
  <div id="app-container">
    <!-- 头部 -->
    <mt-header fixed title="黑马程序员·Vue项目">
      <span slot="left" v-show="flag">
        <mt-button icon="back" @click="RouterBack()">返回</mt-button>
      </span>
    </mt-header>
    <!-- 中间 -->
    <router-view/>
    <!-- tabbar -->
    <nav class="mui-bar mui-bar-tab">
      <router-link class="mui-tab-item" to="/home">
        <span class="mui-icon mui-icon-home"></span>
        <span class="mui-tab-label">首页</span>
      </router-link>
      <router-link class="mui-tab-item" to="/member">
        <span class="mui-icon mui-icon-contact"></span>
        <span class="mui-tab-label">会员</span>
      </router-link>
      <router-link class="mui-tab-item" to="/shopcar">
        <span class="mui-icon mui-icon-extra mui-icon-extra-cart">
          <!-- <template  @back="receive"> -->
            <span class="mui-badge">{{num}}</span>
          <!-- </template> -->
        </span>
        <span class="mui-tab-label">购物车</span>
      </router-link>
      <router-link class="mui-tab-item" to="/search">
        <span class="mui-icon mui-icon-search"></span>
        <span class="mui-tab-label">搜索</span>
      </router-link>
    </nav>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      flag: false,
      num: 0
    };
  },
  methods: {
    RouterBack() {
      this.$router.go(-1);
    },
    receive(k) {
      console.log(k);
      this.num = k;
    }
  },
  watch: {
    $route: function(to, from) {
      // console.log(from.path) //切换前的路由
      // console.log(to.path)   //当前路由
      if (to.path === "/home") {
        this.flag = false;
      } else {
        this.flag = true;
      }
    }
  }
};
</script>

<style lang='less' scope>
#app-container {
  margin-top: 40px;
  background: #fff;
  // height: 100%;
}
</style>
