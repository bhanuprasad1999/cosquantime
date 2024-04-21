<template>
  <q-layout view="hHh lpr lfr">
    <q-header elevated :class="$q.dark.isActive ? 'bg-secondary' : 'bg-blue-grey-7'">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>
          Cosquantime
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="200"
      :breakpoint="500"
      bordered
      :class="$q.dark.isActive ? 'bg-grey-9' : 'bg-grey-3'"
    >
      <q-scroll-area class="fit">
        <q-list>
          <template v-for="(menuItem, index) in menuList" :key="index">
            <q-item clickable :to="menuItem.path" v-ripple>
              <q-item-section avatar>
                <q-icon :name="menuItem.icon"></q-icon>
              </q-item-section>
              <q-item-section>
                {{ menuItem.label }}
              </q-item-section>
            </q-item>
            <q-separator :key="'sep' + index" v-if="menuItem.separator"></q-separator>
          </template>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const leftDrawerOpen = ref<boolean>(false)

const menuList = [
  {
    icon: 'home',
    label: 'Home',
    separator: false,
    path: '/home'
  },
  {
    icon: 'description',
    label: 'Blog',
    separator: false,
    path: '/blog'
  },
  {
    icon: 'folder',
    label: 'Projects',
    separator: true,
    path: '/projects'
  },
  {
    icon: 'settings',
    label: 'Settings',
    separator: false,
    path: '/settings'
  }
]

const toggleLeftDrawer = () => {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>

<style scoped>
/* Add any additional CSS styling here */
</style>
