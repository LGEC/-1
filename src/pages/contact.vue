<template >
<div class="container">

  <div class="top">
    <yd-navbar title="客服咨询" bgcolor="#d94927" color="#fff">
      <section slot="left" @click="handleBack">
        <yd-navbar-back-icon color="#fff"></yd-navbar-back-icon>
      </section>
    </yd-navbar>
  </div>

  <div class="cen">
    <yd-cell-group>

      <yd-cell-item arrow v-for="item,key in data.phoneNo" :key="item">
        <span slot="left">客服电话</span>
        <span slot="right"><a :href="`tel:${item}`">{{item}}</a></span>
      </yd-cell-item>
      <yd-cell-item arrow v-for="item,key in data.qqNo" :key="item">
        <span slot="left">客服Q Q</span>
        <span slot="right"><a :href="`mqqwpa://im/chat?chat_type=wpa&uin=${item}&version=1&src_type=web&web_src=oicqzone.com`">{{item}}</a></span>
      </yd-cell-item>
      <yd-cell-item arrow v-for="item,key in data.wChat" :key="item">
        <span slot="left">客服微信</span>
        <span slot="right">{{item}}</span>
      </yd-cell-item>

    </yd-cell-group>
  </div>


</div>
</template>

<script>
import config from '@/config.js';
export default {
  data () {
    return {
      data:{}
    }
  },
  beforeCreate(){
  },
  created(){
    let url =`${config.host}index.php?m=Mobile&c=Index&a=loadConfigs`;
    this.$http.get(url).then((res)=>{
      // console.log(res.body);
      this.data = res.body;
    // console.log(this.data);
    })
    
  	//微信分享
    let thisUrl = window.location.href;
  // console.log(thisUrl)
    wechatShare({
    	url:thisUrl,
    	title: '分领商城',
    	desc:'分享财富，引领未来',
     	content: '分享财富，引领未来',
     	link: '',
     	logo: '',
    });
  },
  methods: {
    handleBack() {
      this.$router.go(-1);
      // console.log(this.$router);
    }
  }
}
</script>

<style scoped>

</style>
