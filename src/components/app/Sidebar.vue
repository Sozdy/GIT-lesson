<template lang="pug">
  ul.sidenav.app-sidenav(:class="{open: isSidebarOpen}")
    router-link(
      v-for="sidebarLink in sidebarLinks"
      :key="sidebarLink.to"
      tag="li"
      :to="sidebarLink.to"
      active-class="active"
      :exact="sidebarLink.exact")
      a(href="#").waves-effect.waves-orange.pointer {{sidebarLink.title}}

</template>

<script>
  export default {
    name: "Sidebar",

    data: () => ({
      sidebarLinks: [
        {title: 'Счет', to: '/', exact: true},
        {title: 'История', to: '/history', exact: true},
        {title: 'Планирование', to: '/planning', exact: true},
        {title: 'Новая запись', to: '/record', exact: true},
        {title: 'Категории', to: '/categories', exact: true},
      ]
    }),

    props: {
      isSidebarOpen: {
        type: Boolean
      },
    },
  }

</script>

<style scoped>

</style>
