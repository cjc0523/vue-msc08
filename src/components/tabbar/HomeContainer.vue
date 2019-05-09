<template>
  <div>
    <!-- 轮播图 -->
    <!-- <div class="lunbo"> -->
    <mt-swipe :auto="4000">
      <mt-swipe-item v-for="(item,k) in imgs" :key="k" :name="item.id">
        <img :src="item.img">
      </mt-swipe-item>
    </mt-swipe>
    <!-- </div> -->
    <!-- 九宫格改造六宫格 -->
    <div class="mui-content">
      <ul class="mui-table-view mui-grid-view mui-grid-9">
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
          <router-link to="/home/newslist">
            <!-- <span> -->
              <img src="../../images/menu1.png" alt>
            <!-- </span> -->
            <div class="mui-media-body">新闻资讯</div>
          </router-link>
        </li>
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
          <router-link to="/home/photolist">
            <!-- <span> -->
              <img src="../../images/menu2.png" alt>
            <!-- </span> -->
            <div class="mui-media-body">图片分享</div>
          </router-link>
        </li>
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
          <router-link to="/home/goods">
            <!-- <span>/ -->
              <img src="../../images/menu3.png" alt>
            <!-- </span> -->
            <div class="mui-media-body">商品购买</div>
          </router-link>
        </li>
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
          <a href="#">
            <!-- <span> -->
              <img src="../../images/menu4.png" alt>
            <!-- </span> -->
            <div class="mui-media-body">留言反馈</div>
          </a>
        </li>
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
          <a href="#">
            <!-- <span> -->
              <img src="../../images/menu5.png" alt>
            <!-- </span> -->
            <div class="mui-media-body">视频专区</div>
          </a>
        </li>
        <li class="mui-table-view-cell mui-media mui-col-xs-4 mui-col-sm-4">
          <a href="#">
            <!-- <span> -->
              <img src="../../images/menu6.png" alt>
            <!-- </span> -->
            <div class="mui-media-body">联系我们</div>
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  created() {
    this.getLunbo();
  },
  data() {
    return {
      imgs: []
    };
  },
  methods: {
    async getLunbo() {
      const { data: res } = await this.$http.get("/api/getlunbo");
      this.imgs = res.message;
      // console.log(res.message);
    }
  }
};
</script>

<style lang="less">
.mint-swipe {
  height: 200px;
  img {
    width: 100%;
    height: 100%;
  }
}
.mui-content {
  .mui-table-view,
  .mui-grid-view,
  .mui-grid-9 {
    background: #fff;
    border: 0;

    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    .mui-table-view-cell {
      // flex:1;
      width: 85px;
      height: 110px;
      border: 0;
      font-size: 12px !important;
      img {
        width: 100%;
        // height: 100%;/
      }
    }
  }
}
.mui-grid-view,.mui-grid-9:after {
  position: absolute !important;
}
.mui-table-view,.mui-grid-view ,.mui-table-view-cell, .mui-media-body {
  font-size: 12px !important;
}   
</style>
