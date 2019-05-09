<template>
  <div class="shopcar-container">
    <!-- <div></div> -->
    <!-- 卡片区 -->
    <div class="mui-card" v-for="item in message" :key="item.id">
      <!-- <div class="mui-card-content"> -->
      <div class="mui-card-content-inner">
        <!-- <template slot-scope="info"> -->
          <!-- {{info}} -->
          <!-- switch开关-->
          <div class="switch">
            <mt-switch v-model="switchValue"></mt-switch>
          </div>
          <!-- 中间图片 -->
          <div class="img">
            <img :src='item.thumb_path' alt>
          </div>
          <!-- 右侧商品 -->
          <div class="goods">
            <div>
              <!-- title -->
              <h4 class="mui-content-padded">{{item.title}}</h4>
              <!-- 价钱: -->
              <span class="money">
                <span>￥</span>
                {{item.sell_price}}
              </span>
              <!-- 加减框 -->
              <div class="mui-numbox" data-numbox-min="1">
                <button class="mui-btn mui-btn-numbox-minus" type="button" @click="reduce">-</button>
                <input class="mui-input-numbox" type="number" v-model="cou">
                <button class="mui-btn mui-btn-numbox-plus" type="button" @click="add()">+</button>
              </div>
              <!-- 删除 -->
              <span class="del" @click="del()">删除</span>
            </div>
          </div>
        <!-- </template> -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  created() {
    this.getGoodsList();
  },
  data() {
    return {
      switchValue: true,
      cou: 1,
      // countobj:{
      //   count1:1,
      //   count2:1,
      //   count3:1
      // },
      price: 2222,
      title: "",
      message: [],
      num:0
    };
  },
  methods: {
    add() {
      this.cou++;
      // console.log(id);
    },
    reduce() {
      if (this.cou === 1) {
        return false;
      }
      this.cou--;
    },
    async getGoodsList() {
      const { data: res } = await this.$http.get(
        "/api/goods/getshopcarlist/87,88,89"
      );
      console.log(res.message);
      this.message = res.message;
      this.num = res.message.length
      console.log(this.num)
      // this.cou = res.message.cou
    }
  }
};
</script>

<style lang="less">
.shopcar-container {
  margin-top: 50px;
  .mui-card {
    margin-top: 10px;
  }
}
.mui-card {
  height: 100px;
  .mui-card-content-inner {
    height: 100%;
    display: flex;
    // justify-content: space-between;
    align-items: center;
    padding: 10px;
    .img {
      width: 60px;
      margin-right: 10px;
      img {
        width: 100%;
      }
    }
    .switch {
      // width: 60px;
      margin-right: 10px;
    }
    .goods {
      width: 270px;
      right: 0px;
      p {
        margin: 0;
      }
      h4 {
        font-size: 14px;
      }
      .money,
      .del {
        color: red;
        font-weight: 700;
        font-size: 14px;
      }
      .del {
        color: #007aff;
      }
    }
  }
}
.mui-numbox {
  width: 85px;
  padding: 0 25px;
  height: 27px;
  line-height: 27px;
  .mui-btn {
    width: 25px;
    // height: 20px;
  }
}
</style>
