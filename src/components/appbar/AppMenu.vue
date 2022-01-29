<template>
  <div class="menu">
      <button @click="toggleMenu" :class="{open : open}">
          <span class="first-span"></span>
          <span v-if="!open"></span>
          <span class="second-span"></span>
      </button>
      <div class="menu-drawer" :class="{'menu-drawer__expanded': open}">
          <div v-for="(item, idx) in menuItems" :key="idx" @click="item.action">
              {{ item.title }}
          </div>
      </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface MenuItem {
    title: string;
    action?: () => void;
}

const props = defineProps<{
    menuItems: MenuItem[]
}>()

const open = ref(false);

function toggleMenu() {
    open.value = !open.value;
}

function closeMenu() {
    open.value = false;
}
</script>

<style scoped lang="scss">
@import '../../styles/borders.scss';
@import '../../styles/colors.scss';
.menu {
    button {
        width: 30px;
        height: 30px;
        background-color: $white;
        border-radius: $app-border-radius;
        border: none;
        z-index: 600;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-around;
        padding: 5px 0;
        cursor: pointer;
        span {
            width: 60%;
            border: $app-border;
            transition: transform 0.3s linear;
        }
        &.open{
            justify-content: space-between;
            padding-left: 7px;
            span {
                width: 100%;
                transform: translateX(5px);
            }
            .first-span {
                transform: rotate(45deg);
                transform-origin: bottom left;
            }
            .second-span {
                transform: rotate(-45deg);
                transform-origin: top left;
            }
        }     
    }

    &-drawer {
        position: fixed;
        top: 50px;
        left: 100vw;
        background-color: silver;
        height: calc(100vw - 50px);
        width: 300px;
        transition: all 0.5s;
        &__expanded {
            left: calc(100vw - 300px);
        }
        // transform: translateX(-50%);

    }
}
</style>