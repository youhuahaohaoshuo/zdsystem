<template>
  <div id="app" class="app-main">
    <router-view @loginOut="loginOut"/>
  </div>
</template>

<script>
  import {outLogin} from '@/api/request'

  export default {
    name: 'app',
    methods: {
      loginOut() {
        outLogin().then(data => {
          if (data !== 'isError') {
            this.$router.replace({name: 'login'})
            window.sessionStorage.clear()
            window.location.reload()
          }
        })
      }
    }
  }
</script>

<style lang="less">
  html, body {
    width: 100%;
    height: 100%;
    overflow: hidden;
    font-size: 14px;
  }

  .app-main {
    width: 100%;
    height: 100%;
  }

  .handle-wrapper {
    display: flex;
    padding-right: 12px;
    span + span {
      margin-left: 30px;
      cursor: pointer;
    }
  }
  .btn-wrapper {
    margin-bottom: 5px;
    padding: 8px 30px;
    background-color: #fff;
  }
</style>
