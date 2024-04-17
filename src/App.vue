<template>
  <AppContent/>
  <AppFooter/>
</template>

<script>
import AppContent from './components/AppContent.vue';
import AppFooter from './components/AppFooter.vue';

export default {
  components: {
    AppContent,
    AppFooter,
  }
}
</script>
<style lang="scss">
@use './style/general.scss';
</style>
