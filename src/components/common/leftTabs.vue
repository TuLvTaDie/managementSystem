<template>
  <el-row class="tac">
    <el-col :span="24">
      <el-menu
        default-active="2"
        class="el-menu-vertical-demo"
        @open="handleOpen"
        @close="handleClose"
        v-for="(item, index) in props.data"
        :key="item.id+index"
      >
        <el-sub-menu :index="item.id">
          <template #title>
            <el-icon><location /></el-icon>
            <span>{{ item.label }}</span>
          </template>
          <div v-for="(secondItem, secondIndex) in item.children" :key="secondIndex">
            <el-sub-menu v-if="secondItem.children.length" :index="secondItem.id">
              <template #title>
                <span>{{ secondItem.label }}</span>
              </template>
              <el-menu-item v-for="(thirdlyItem, thirdlyIndex) in secondItem.children" :key="thirdlyIndex" :index="thirdlyItem.id">{{ thirdlyItem.label }}</el-menu-item>
            </el-sub-menu>
          </div>
          <el-menu-item-group v-for="(secondItem, secondIndex) in item.children" :key="secondIndex">
              <el-menu-item v-if="!secondItem.children.length" :index="secondItem.id">{{ secondItem.label }}</el-menu-item>
          </el-menu-item-group>
        </el-sub-menu>

        <!-- <el-sub-menu index="2">
          <template #title>
            <el-icon><location /></el-icon>
            <span>Navigator One</span>
          </template>
          <el-menu-item-group>
            <el-menu-item index="2-1">item one</el-menu-item>
            <el-menu-item index="2-2">item two</el-menu-item>
            <el-menu-item index="2-3">item three</el-menu-item>
          </el-menu-item-group>
          <el-sub-menu index="2-4">
            <template #title>item four</template>
            <el-menu-item index="2-4-1">item one</el-menu-item>
          </el-sub-menu>
        </el-sub-menu> -->
        <!-- <el-sub-menu index="2">
          <template #title>
            <el-icon><icon-menu /></el-icon>
            <span>Navigator Two</span>
          </template>
          <el-menu-item-group>
            <el-menu-item index="2-1">item one</el-menu-item>
            <el-menu-item index="2-2">item two</el-menu-item>
            <el-menu-item index="2-3">item three</el-menu-item>
          </el-menu-item-group>
        </el-sub-menu>
        <el-menu-item index="3" disabled>
          <el-icon><document /></el-icon>
          <span>Navigator Three</span>
        </el-menu-item>
        <el-menu-item index="4">
          <el-icon><setting /></el-icon>
          <span>Navigator Four</span>
        </el-menu-item> -->
      </el-menu>
    </el-col>
  </el-row>
</template>

<script lang="ts">
  import { defineComponent } from 'vue'
  export default defineComponent({
    name: 'leftTabs',
  })
</script>

<script lang="ts" setup>
  import { defineProps, PropType } from 'vue'
  export interface ColumnProps{
    id: any,
    path: any,
    name: any,
    label: any,
    icon: any,
    url: any,
    router: any,
    children: any
  }
  import {
    Document,
    Menu as IconMenu,
    Location,
    Setting,
  } from '@element-plus/icons-vue'

  const props = defineProps({
    data: {
      type: Array as PropType<ColumnProps[]>,
      default: () => []
    }
  });
  const handleOpen = (key: string, keyPath: string[]) => {
    console.log(key, keyPath)
  }
  const handleClose = (key: string, keyPath: string[]) => {
    console.log(key, keyPath)
  }
</script>

<style lang="scss">
  .el-menu-item-group__title {
    display: none;
  }
  .el-menu-item:hover {
    color: rgba($color: #409EFF, $alpha: 0.7);
    background-color: rgba($color: #409EFF, $alpha: .1)
  }
</style>