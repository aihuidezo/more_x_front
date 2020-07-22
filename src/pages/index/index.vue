<template>
  <div>
    <div v-if="notLogin">
      <login @loginsuccess="loginSuccess"></login>
    </div>

  </div>
</template>

<script>
  import login from "../../components/login";

export default {

  components:{
      login
  },

  data () {
    return {
      notLogin:true
    }
  },
  //函数在页面加载完成后执行
  mounted(){
   if (wx.getStorageSync('userinfo')){
       this.notLogin=false
   }else {
       wx.hideTabBar()
   }

  },
  methods:{
    loginSuccess(){
        this.notLogin=false
        wx.showTabBar()
        wx.showToast({
            title: '登录成功',
            icon: 'success',
            duration: 2000
        })
    }
  }

}
</script>

<style scoped lang="scss">

</style>
