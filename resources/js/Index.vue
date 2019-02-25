<template>
    <div id="main">
        <nav class="navbar navbar-expand-md navbar-light navbar-laravel">
            <navigationMenu></navigationMenu>
        </nav>
        <!-- <div id="content"> -->
        <main class="py-4">
            <router-view></router-view>
        </main>
        <!-- </div> -->
    </div>
</template>
<script>
  import navigationMenu from './components/Menu.vue'
  export default {
    data() {
      return {
        //
      }
    },
    components: {
      navigationMenu
    }
  }
</script>
