<script setup lang="ts">
console.log("hello block")
</script>

<template>
  <div class="block">
    <slot />
  </div>
</template>

<style scoped lang="scss">
.block {
  margin-top: 80px;

  > .title {
    font-weight: 700;
    margin-bottom: 24px;
  }

  > .text {

    margin-bottom: 16px;

    &:last-child {
      margin-bottom: 0;
    }
  }

  > .list {
    margin-bottom: 16px;
  }
}
</style>