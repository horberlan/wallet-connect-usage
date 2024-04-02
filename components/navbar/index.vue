<template>
  <nav
    :class="
      css({
        display: 'flex',
        justifyContent: 'space-between',
        paddingInline: '2',
        paddingBlock: '1',
      })
    "
  >
    <ul>
      <li v-for="(item, index) in menuItems" :key="index">
        {{ item.label }}
      </li>
    </ul>
    <OpenModal />
  </nav>
</template>

<script setup lang="ts">
import { css } from "styled-system/css";

const OpenModal = defineAsyncComponent(() => import("./OpenModal.vue"));
const menuItems = [
  { label: "link", alt: "_to" },
  { label: "link", alt: "_to" },
  { label: "link", alt: "_to" },
];
</script>
