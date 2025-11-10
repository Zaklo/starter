<script setup lang="ts">
const route = useRoute()

const { data: page } = await useAsyncData('page-' + route.path, () => {
  return queryCollection('content').path(route.path).first()
})

if (!page.value) {
  throw createError({ statusCode: 404, statusMessage: 'Page not found', fatal: true })
}
</script>

<template>
  <div class="main">
    <ContentRenderer
      v-if="page"
      :value="page"
    />
  </div>
</template>

<style lang="scss">
.main {
  padding: 0 20px;

  @include media('>=tablet') {
    padding: 0 124px;
  }

  @include media('>=desktop') {
    padding: 0;
    max-width: 446px;
    margin: auto;
  }

  > .block {
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
}
</style>
