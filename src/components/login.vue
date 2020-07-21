<template>
    <div>
      <button open-type="getUserInfo" @getuserinfo="getUserInfo">授权登录</button>
    </div>
</template>

<script>
  import config from "../config";
  export default {
      methods:{
          getUserInfo(e){
              console.log(e.target.userInfo)
              const loginUrl=config.loginUrl
              wx.login({
                  success (res) {
                      console.log(res)
                      if (res.code) {
                          //发起网络请求
                          wx.request({
                              url: loginUrl,
                              data: {
                                  code: res.code
                              }
                          })
                      } else {
                          console.log('登录失败！' + res.errMsg)
                      }
                  }
              })
          }
      }
  }
</script>

<style scoped lang="scss">

</style>
