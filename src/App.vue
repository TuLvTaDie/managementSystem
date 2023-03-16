<template>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav>
  <router-view/> -->
  <div id="app">
    <div class="header"></div>
    <div class="body">
      <div class="leftTabs">
        <leftTabs :data="menuList"/>
      </div>
      <div class="pageBody"></div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from 'vue';
import leftTabs from '@/components/common/leftTabs.vue';
export default defineComponent({
  components: {
    leftTabs
  },
  setup() {
    let menuList: any = [
      {
        id: '1',
        path: '/CityShow',
        name: 'HomeFilled',
        label: '首页',
        icon: 'HomeFilled',
        url: '/CityShow',
        router: '',
        children: [{
            id: '1-2',
            path: '/page2',
            name: 'page2',
            label: 'page2',
            url: '/page2',
            children: [
              {
                id: '1-1-1',
                path: '/page1',
                name: 'page1',
                label: 'page1',
                url: '/page1',
              },
            ],
          },],
      },
      {
        id: '2',
        path: '/UserFilled',
        name: 'UserFilled',
        label: '用户管理',
        icon: 'UserFilled',
        url: '/UserFilled',
        children: [ 
          {
            id: '2-2',
            path: '/page2',
            name: 'page2',
            label: 'page2',
            url: '/page2',
            children: [
              {
                id: '2-1-1',
                path: '/page1',
                name: 'page1',
                label: 'page1',
                url: '/page1',
              },
            ],
          },
        ],
      },
      {
        id: '3',
        path: '/Management',
        name: 'Management',
        label: '订单管理',
        icon: 'Management',
        url: '/Management',
        children: [],
      }
    ]
    return {
      menuList,
    }
  }
})
</script>
<style lang="scss">
body {
  margin: 0;
  padding: 0;
}

#app {
  width: 100vw;
  height: 100vh;
  .header {
    width: 100%;
    height: 80px;
    height: 5rem;
    background-color: red;
  }

  .body {
    width: 100%;
    height: calc(100% - 80px);
    height: calc(100% - 5rem);
    display: flex;
    .leftTabs {
      width: 10%;
      height: 100%;
      background-color: #ffffff;
    }
    .pageBody {
      width: 90%;
      height: 100%;
      background-color: yellowgreen;
    }
  }
}
</style>
