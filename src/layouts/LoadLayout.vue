<template>
  <div class="loading-layout">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'LoadLayout'
}
</script>
<style lang="stylus">
.loading-layout {
   height: 100vh;
}
</style>
