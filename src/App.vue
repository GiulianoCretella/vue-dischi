<template>
  <div id="app">
    <app-header/>
    <main>
      <app-main/>
    </main>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppMain from './components/AppMain.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain,
  }
}
</script>

<style lang="scss">
@import './style/general.scss';
#app{
  background-color: $app-bg-color;
  height: 100vh;
  overflow-y:auto ;
}
</style>
