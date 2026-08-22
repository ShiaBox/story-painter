<script setup lang="ts">
import Main from "~/Main.vue";
import { darkTheme, lightTheme } from "naive-ui";
import type { GlobalThemeOverrides } from "naive-ui";
import { computed } from "vue";

import { useDark } from '@vueuse/core'

const isDark = useDark({ disableTransition: false })

// Dice-Next 设计系统：indigo 主色 + 0.5rem 圆角体系，与 Dice-Next-WebUI 对齐
const themeOverrides = computed<GlobalThemeOverrides>(() => {
  const dark = isDark.value
  return {
    common: {
      primaryColor: dark ? '#818cf8' : '#4f46e5',
      primaryColorHover: dark ? '#a5b4fc' : '#4338ca',
      primaryColorPressed: dark ? '#6366f1' : '#3730a3',
      primaryColorSuppl: dark ? '#818cf8' : '#4f46e5',
      infoColor: dark ? '#818cf8' : '#4f46e5',
      infoColorHover: dark ? '#a5b4fc' : '#4338ca',
      infoColorPressed: dark ? '#6366f1' : '#3730a3',
      infoColorSuppl: dark ? '#818cf8' : '#4f46e5',
      errorColor: dark ? '#f87171' : '#ef4444',
      errorColorHover: dark ? '#fca5a5' : '#dc2626',
      errorColorPressed: dark ? '#ef4444' : '#b91c1c',
      errorColorSuppl: dark ? '#f87171' : '#ef4444',
      successColor: dark ? '#4ade80' : '#22c55e',
      warningColor: dark ? '#facc15' : '#eab308',
      borderRadius: '6px',
      borderRadiusSmall: '4px',
      fontFamily: "Inter, system-ui, -apple-system, 'PingFang SC', 'Hiragino Sans GB', 'Microsoft YaHei', sans-serif",
      fontWeightStrong: '600',
      borderColor: 'hsl(var(--border))',
      dividerColor: 'hsl(var(--border))',
    },
  }
})
</script>

<template>
  <n-config-provider :theme="isDark ? darkTheme : lightTheme" :theme-overrides="themeOverrides">
    <n-message-provider>
      <n-modal-provider>
        <n-notification-provider>
          <Main/>
        </n-notification-provider>
      </n-modal-provider>
    </n-message-provider>
  </n-config-provider>
</template>
