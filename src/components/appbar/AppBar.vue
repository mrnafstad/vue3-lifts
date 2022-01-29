<template>
  <div class="app-bar">
      <div class="page-title">
          title
      </div>
      <div class="app-menu">
          <app-menu :menu-items="menuItems"></app-menu>
      </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import AppMenu from './AppMenu.vue';

const menuItems = ref([
    {
        title: 'First',
        action: () => {
            window.alert('First was clicked')
        }
    },
    {
        title: 'Second',
        action: () => {
            window.alert('Second was clicked')
        }
    },
    {
        title: 'Third',
        action: () => {
            window.alert('Third was clicked')
        }
    }
])
</script>

<style scoped lang="scss">
@import '../../styles/colors.scss';
.app-bar {
    position: absolute;
    top: 0px;
    background-color: $black;
    color: $white;
    height: 50px;
    width: 100vw;
    display: flex;
    align-items: center;
    z-index: 500;
    justify-content: space-between;
}

.page-title {
    margin-left: 8px;
}

.app-menu {
    margin-right: 8px;
}
</style>