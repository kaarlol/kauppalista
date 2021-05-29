<template>
  <v-app>
    <v-navigation-drawer app v-model="drawer">
    </v-navigation-drawer>

    <v-app-bar color="green" app dark>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
    </v-app-bar>

    <v-main>
        <Nuxt />
    </v-main>

  </v-app>
</template>

<script>
export default {
    data: () => ({
      drawer: false,
      group: null
    }),

    watch: {
      group () {
        this.drawer = false
      },
    },
  }
</script>
