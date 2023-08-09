<template>
  <q-layout>

    <q-header class="bg-primary" :bordered="true">
      <q-toolbar>
        <!-- <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" /> -->
        <!-- <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg"> -->
        <q-icon size="2rem">
          <LogoIcon />
        </q-icon>
        <q-toolbar-title class="text-black text-bold text-h6 text-weight-medium">
          ВСОЦ.СЕТИ
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" side="left" overlay behavior="desktop" bordered>
      <q-list padding class="text-grey-8">
        <q-item class="GNL__drawer-item" v-for="navItem in navList" :key="navItem.text" clickable>
          <q-item-section avatar>
            <q-icon size="1.5rem">
              <component :is="navItem.icon" />
            </q-icon>
          </q-item-section>
          <q-item-section>
            <q-item-label class="text-black text-h7 text-weight-regular">{{ navItem.text }}</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <slot />
    </q-page-container>

  </q-layout>
</template>
  
<script setup lang="ts">
import { ref } from 'vue'
import { FriendsIcon, GalleryIcon, LogoIcon, MessageIcon, NewsIcon, ProfileIcon, SomeIcon } from "@/components/icons/index"

const leftDrawerOpen = ref(true)

interface NavItem {
  text: string,
  icon: typeof SomeIcon
}

const navList: NavItem[] = [
  {
    text: "Моя страница",
    icon: ProfileIcon
  },
  {
    text: "Сообщения",
    icon: MessageIcon
  },
  {
    text: "Друзья",
    icon: FriendsIcon
  },
  {
    text: "Галерея",
    icon: GalleryIcon
  },
  {
    text: "Новости",
    icon: NewsIcon
  }
]
</script>