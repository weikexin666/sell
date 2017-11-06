<template>
  <div id="app">
    <myHeader :seller="seller"></myHeader>
    <div class="tab">
      <div class="tab-item"><router-link to="/">商品</router-link></div>
      <div class="tab-item"><router-link to="/ratings">评价</router-link></div>
      <div class="tab-item"><router-link to="/seller">商家</router-link></div>
    </div>
    <div class="content">
      <router-view/>
    </div>
  </div>
</template>

<script>
import myHeader from '@/components/header/header'
import axios from 'axios'
const ERR_OK = 20000
const URL = 'https://easy-mock.com/mock/59ffc8b886bed60940101d3e/sell/baseData'

export default {
  name: 'app',
  data () {
    return {
      seller: {}
    }
  },
  components: {
    myHeader
  },
  created () {
    axios.get(URL).then((res) => {
      if (res.data.code === ERR_OK) {
        console.log(res.data)
        this.seller = res.data.seller
      }
    })
  }
}
</script>

<style lang="scss" scoped>
@import "./common/css/mixin.scss";
#app {
  .tab{
    display: flex;
    line-height: 40px;
    width: 100%;
    height: 40px;
    @include borderBtm(rgba(7,17,27,.1));
    .tab-item{
      flex: 1;
      height: 100%;
      text-align: center;
    }
  }
}

</style>
