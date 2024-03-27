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
    <li> Brand</li>
  </ul>
    <OpenModal />
  </nav>
</template>

<script setup lang="ts">
import { css } from "styled-system/css";

const OpenModal = defineAsyncComponent(() => import("./OpenModal.vue"));
</script>
