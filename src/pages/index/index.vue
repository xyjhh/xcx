<script setup lang="ts">
//
import { onLoad } from '@dcloudio/uni-app'
import XtxSwiper from '@/components/XtxSwiper.vue'
import { getHomeBannerAPI, getHomeCategoryAPI } from '@/services/home'
import CategoryPanel from '@/pages/index/components/CategoryPanel.vue'
import CustomNavbar from '@/pages/index/components/CustomNavbar.vue'
import type { BannerItem, CategoryItem } from '@/types/home'
import { ref } from 'vue'
const bannerList = ref<BannerItem[]>([])
const getHomeBannerdata = async () => {
  const res = await getHomeBannerAPI()
  bannerList.value = res.result
}
const categoryList = ref<CategoryItem[]>([])
const getHomeCategoryData = async () => {
  const res = await getHomeCategoryAPI()
  categoryList.value = res.result
}
onLoad(() => {
  getHomeBannerdata()
  getHomeCategoryData()
})
</script>

<template>
  <CustomNavbar></CustomNavbar>
  <XtxSwiper :list="bannerList"></XtxSwiper>
  <CategoryPanel :list="categoryList"></CategoryPanel>
</template>

<style lang="scss">
page {
  background-color: #f7f7f7;
}
</style>
