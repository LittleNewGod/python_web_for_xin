<template>
  <div id="app">
    <!-- exclude的作用是排除这个组件名不做缓存，其他的依然做缓存 -->
    <keep-alive exclude="Detail">
      <router-view/>
    </keep-alive>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
</style>
