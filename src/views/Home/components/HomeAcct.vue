<script setup lang="ts">
import Button from '@/components/base/BaseButton.vue'
import BaseLink from '@/components/base/BaseLink.vue'
import { ArrowUpRightIcon, ArrowDownTrayIcon } from '@heroicons/vue/24/outline'
import { useRouter } from 'vue-router'

const linkList = [
  {
    icon: ArrowUpRightIcon,
    title: '向朋友轉帳',
    subtitle: '簡單又免費',
    path: 'NtdTransfer'
  },
  {
    icon: ArrowDownTrayIcon,
    title: '明細查詢',
    subtitle: '查看最近的交易紀錄',
    path: 'History'
  }
]

const router = useRouter()
const goLink = (name: string): void => {
  router.push({ name })
}
</script>

<template>
  <div class="p-4">
    <h2 class="mb-6 text-2xl font-bold">{{ $t('現金') }}</h2>
    <h3 class="mb-6 text-xl font-bold">{{ $t('現金餘額') }}</h3>
    <h1 class="my-6 text-3xl font-bold">$1450</h1>
    <div class="my-4 grid grid-flow-col gap-4">
      <Button @click="goLink('NtdAcct')">{{ $t('查看帳號') }}</Button>
      <Button>{{ $t('提款') }}</Button>
    </div>
    <div>
      <BaseLink v-for="(item, index) in linkList" :key="index" :icon="item.icon" :title="item.title" :subtitle="item.subtitle" :path="item.path" />
    </div>
  </div>
</template>

