<template>
  <div class="header">
    <div class="content-wrapper">
      <div class="avatar">
        <img :src="seller.avatar" width="64" height="64">
      </div>
      <div class="content">
        <div class="title">
          <span class="brand" v-if="seller.brand"></span>
          <span class="name">{{seller.name}}</span>
        </div>
        <div class="description">
          <span>{{seller.description}}/{{seller.deliveryTime}}分钟送达</span>
        </div>
        <div class="support" style="margin-top:10px" v-if="seller.supports">
          <i class="icon" :class="classMap[seller.supports[0].type]"></i>
          <span class="text">{{seller.supports[0].description}}</span>
        </div>
      </div>
      <div class="support-num" v-if="seller.supports">
        <span class="count">{{seller.supports.length}}个</span>
        <i class="iconfont icon-arrow-right"></i>
      </div>
    </div>
    <div class="bulletin-wrapper">
      <span class="bulletin-title">
      </span>
      <span class="bulletin-text">
        {{seller.bulletin}}
      </span>
      <i class="iconfont icon-arrow-right"></i>
    </div>
    <div class="background">
      <img :src="seller.avatar" width="100%">
    </div>
  </div>
</template>

<script type="text/javascript">
export default {
  props: {
    seller: {
      type: Object
    }
  },
  data () {
    return {
    }
  },
  created () {
    this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
  }
}
</script>

<style lang="scss">
@import "../../common/css/mixin.scss";
.header{
  color: #fff;
  overflow: hidden;
  position: relative;
  background: rgba(7,17,27,.5);
  .content-wrapper{
    width: 100%;
    padding: 24px 12px 18px 24px;
    position: relative;
    overflow: hidden;
    font-size: 0;
    .avatar{
      display: inline-block;
      img{
        border-radius: 2px;
      }
    }
    .content{
      margin-left: 16px;
      display: inline-block;
      overflow: hidden;
      font-size: 10px;
      vertical-align: top;
      .title{
        .brand{
          width: 30px;
          height: 18px;
          display: inline-block;
          @include bgImg('brand');
        }
        .name{
          font-size: 16px;
          font-weigth: bold;
          line-height: 18px;
          vertical-align: top;
        }
      }
      .description{
        font-size: 12px;
        font-weight: 200;
        line-height: 12px;
        margin-top: 8px;
      },
      .support{
        .icon{
          width: 12px;
          height: 12px;
          display: inline-block;
        }
        .text{
          margin-top: 10px;
          vertical-align: top;
          font-size: 10px;
          font-weight: 200;
          line-height: 12px;
        }
        &.decrease{
          @include bgImg(decrease_1);
        }
        &.discount{
          @include bgImg(discount_1);
        }
        &.special{
          @include bgImg(special_3);
        }
        &.invoice{
          @include bgImg(invoice_1);
        }
        &.guarantee{
          @include bgImg(guarantee_1);
        }
      }
    }
    .support-num{
      position: absolute;
      right: 50px;
      bottom: 20px;
      padding: 0 8px;
      height: 24px;
      line-height: 24px;
      border-radius: 14px;
      font-size: 10px;
      background: rgba(0, 0, 0, .2);
      text-align: center;
      .icon-arrow-right{
        font-size: 10px;
        font-weight: 100;
      }
    }
  }
  .bulletin-wrapper{
    height: 28px;
    padding: 0px 12px 0px 12px;
    background: rgba(7,17,27,0.2);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    position: relative;
    .bulletin-title{
      display: inline-block;
      margin-top: 8px;
      width: 22px;
      height: 12px;
      vertical-align: top;
      @include bgImg(bulletin);
    }
    .bulletin-text{
      line-height: 28px;
      font-size: 10px;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    .icon-arrow-right{
      position: absolute;
      right: 10px;
      top: 7px;
    }
  }
  .background{
    position: absolute;
    top: 0px;
    left: 0px;
    z-index: -1;
    width: 100%;
    height: 100%;
    filter: blur(10px);
  }
}
.router-link-exact-active{
  color: rgb(240,20,20);
}
</style>
