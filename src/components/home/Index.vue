<template>
  <a-layout id="components-layout-demo-custom-trigger">
    <a-layout-sider class="layoutLeft" v-model="collapsed" :trigger="null" collapsible>
      <div class="logo" :style="getStyle()">
        <div class="login_title" v-if="logintitle">
          联合特钢
        </div>
      </div>

      <left-menu></left-menu>

    </a-layout-sider>
    <a-layout>
     
        <a-layout-header style="background: #fff;
                                padding: 0;
                                display:flex;
                                align-items: center;
                                justify-content: space-between;
                                flex-flow:row wrap;">
          <div class="layout_shrink">
            <a-icon
              class="trigger"
              :type="collapsed ? 'menu-unfold' : 'menu-fold'"
              @click="() =>{
                  collapsed = !collapsed
                  logintitle = !logintitle
                  
                  
              }"
            />
            <a-breadcrumb class="layout_shrink_bread">
              <a-breadcrumb-item>隐患上报系统</a-breadcrumb-item>
              <a-breadcrumb-item><a href="">系统管理</a></a-breadcrumb-item>
            </a-breadcrumb>
          </div>

        

          <div class="menu">
            <a-dropdown>
              <a class="ant-dropdown-link"  style="width:7rem !important" @click="e => e.preventDefault()">
                <a-icon type="user" style="color: rgba(24,144,120,.95)"/>&nbsp;炼铁厂-数字信息化部-张莫某<a-icon type="down" />
              </a>
              <a-menu slot="overlay">
                <a-menu-item>
                  <a href="javascript:;">个人中心</a>
                </a-menu-item>
                <a-menu-item>
                  <a href="javascript:;">退出登录</a>
                </a-menu-item>
              </a-menu>
            </a-dropdown>
          </div>
      </a-layout-header>
      <a-layout-content
        :style="{ margin: '24px 16px', padding: '24px', background: '#fff', minHeight: '53rem' }"
      >
        <router-view></router-view>
      </a-layout-content>
    </a-layout>
  </a-layout>
</template>
<script>
  import LeftMenu from './Menu.vue'

  export default {
    name:'Index',
    components: {
      LeftMenu
    },
    data() {
      return {
        collapsed: false,
        menu_isshow: false,
        logintitle:true
      }
    },
    methods:{
      getStyle(){
        if(this.logintitle == false){
          return "background-position: 48% 50%;"
        }else{
          return "background-position: 20% 50%;"
        }
      }
    },
    mounted(){
      console.log(this.$route)
    }

  };
</script>
<style>
  #components-layout-demo-custom-trigger .trigger {
    font-size: 1rem;
    line-height: 3.5rem;
    padding: 0 1.1rem;
    cursor: pointer;
    transition: color 0.3s;
  }

  #components-layout-demo-custom-trigger .trigger:hover {
    color: #1890ff;
  }

  #components-layout-demo-custom-trigger .logo {
    height: 3rem;
    background:url('../../assets/favicon.png') no-repeat;
    background-size: 1rem 1rem;
    background-position: 20% 50%;
    background-color:rgba(0, 0, 0, 0.65);;
  }

  .layoutHeader{
    width:100%;
    height:4rem !important;
  }
  .layoutContent{
    width:100%;
    height:40rem;
  }

  .layoutLeft{
      min-width: 80px !important;
  }

  .login_title{
    font-size:1rem;
    height:3rem !important;
    line-height: 3rem !important;
    color:white;
    text-align: center;
  }

  

  /* 菜单 */
  .menu{
    width:18rem;
    height:3rem;
    margin-right: 1rem;
    text-align:right;
    line-height:3rem;
  }
  ul {
    list-style:none;
    margin:0px;
  }

  .layout_shrink{
    display:flex;
    width:23rem;
    height:3rem;
    justify-content: flex-start;
    align-items: center;
    flex-direction: row;
  }


  .layout_shrink_bread{
    width:15rem;
    height:3rem;
    margin-top: 1.4rem !important;
  }
  
</style>
