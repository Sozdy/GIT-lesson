<template lang="pug">
  div.app-main-layout

    navbar(@sidebarBurgerClick="isSidebarOpen = !isSidebarOpen")

    sidebar(:isSidebarOpen="isSidebarOpen")

    main.app-content(:class="{full: !isSidebarOpen}")
      .app-page
        router-view

    div.fixed-action-btn
      router-link.btn-floating.btn-large.blue(to="/record")
        i.large.material-icons add

</template>

<script>
  import Navbar from "../components/app/Navbar";
  import Sidebar from "../components/app/Sidebar";
    export default {
      name: "MainLayout",
      components: {
        Navbar,
        Sidebar
      },
      data() {
        return {
          isSidebarOpen: true
        }
      },

    }
</script>

<style scoped lang="stylus">

</style>
