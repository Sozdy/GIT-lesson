<template lang="pug">
  nav.navbar.orange.lighten-1
    div.nav-wrapper
      div.navbar-left
        a(href='#' @click.prevent="$emit('sidebarBurgerClick')")
          i.material-icons.black-text dehaze
        span.black-text {{ date | dateFilter("datetime") }}

      ul.right.hide-on-small-and-down
        li
          a.dropdown-trigger.black-text(
            ref="dropdown"
            href="#"
            data-target="dropdown"
          ) USER NAME
            i.material-icons.right arrow_drop_down

          ul#dropdown.dropdown-content
            li
              a.black-text(href="#")
                i.material-icons account_circle
                | Профиль
            li.divider(tabindex="-1")
            li
              router-link.black-text(to="/login?message=Ну_и_катись")
                i.material-icons assignment_return
                | Выйти

</template>

<script>
    export default {
      data() {
        return {
          date: new Date(),
          dateInterval: null,
          dropdown: null
        }
      },

      name: "Navbar",

      mounted() {
        this.dateInterval = setInterval(() => {
            this.date = new Date()
          }, 1000)

        this.dropdown = M.Dropdown.init(this.$refs.dropdown);
      },

      beforeDestroy() {
        clearInterval(this.dateInterval)

        if (this.dropdown && this.dropdown.destroy)
          this.dropdown.destroy()
      },

      filters: {
        dateFilter(date, format='date') {
          const options = {}

          if (format.includes("date")) {
            options.year = "numeric"
            options.month = "long"
            options.day = "numeric"
          }

          if (format.includes("time")) {
            options.hour = "numeric"
            options.minute ="numeric"
            options.second = "numeric"
          }

          return date.toLocaleString('ru-RU', options)
        }
      }
    }
</script>

<style scoped>

</style>
