<script lang="ts" setup>
import { useRoute } from 'vue-router'
import AccountSettingAccount from '@/views/setting/AccountSettingAccount.vue'
import AccountSettingNotification from '@/views/setting/AccountSettingNotification.vue'
import AccountSettingRule from '@/views/setting/AccountSettingRule.vue'
import AccountSettingSite from '@/views/setting/AccountSettingSite.vue'
import AccountSettingWords from '@/views/setting/AccountSettingWords.vue'
import AccountSettingLogging from '@/views/setting/AccountSettingLogging.vue'
import AccountSettingAbout from '@/views/setting/AccountSettingAbout.vue'

const route = useRoute()

const activeTab = ref(route.params.tab)

// tabs
const tabs = [
  {
    title: '用户',
    icon: 'mdi-account',
    tab: 'account',
  },
  {
    title: '站点',
    icon: 'mdi-web',
    tab: 'site',
  },
  {
    title: '规则',
    icon: 'mdi-filter-cog',
    tab: 'filter',
  },
  {
    title: '通知',
    icon: 'mdi-bell',
    tab: 'notification',
  },
  {
    title: '词表',
    icon: 'mdi-file-word-box',
    tab: 'words',
  },
  {
    title: '日志',
    icon: 'mdi-text-box',
    tab: 'logging',
  },
  {
    title: '关于',
    icon: 'mdi-information',
    tab: 'about',
  },
]
</script>

<template>
  <div>
    <VTabs v-model="activeTab" show-arrows>
      <VTab v-for="item in tabs" :key="item.icon" :value="item.tab">
        <VIcon size="20" start :icon="item.icon" />
        {{ item.title }}
      </VTab>
    </VTabs>
    <VDivider />

    <VWindow v-model="activeTab" class="mt-5 disable-tab-transition">
      <!-- Account -->
      <VWindowItem value="account">
        <transition name="fade-slide" appear>
          <AccountSettingAccount />
        </transition>
      </VWindowItem>

      <!-- System -->
      <VWindowItem value="site">
        <transition name="fade-slide" appear>
          <AccountSettingSite />
        </transition>
      </VWindowItem>

      <!-- Notification -->
      <VWindowItem value="filter">
        <transition name="fade-slide" appear>
          <AccountSettingRule />
        </transition>
      </VWindowItem>

      <!-- Notification -->
      <VWindowItem value="notification">
        <transition name="fade-slide" appear>
          <AccountSettingNotification />
        </transition>
      </VWindowItem>
      <!-- Words -->
      <VWindowItem value="words">
        <transition name="fade-slide" appear>
          <AccountSettingWords />
        </transition>
      </VWindowItem>
      <!-- Logging -->
      <VWindowItem value="logging">
        <transition name="fade-slide" appear>
          <AccountSettingLogging />
        </transition>
      </VWindowItem>
      <!-- About -->
      <VWindowItem value="about">
        <transition name="fade-slide" appear>
          <AccountSettingAbout />
        </transition>
      </VWindowItem>
    </VWindow>
  </div>
</template>
