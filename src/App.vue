<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      app
      temporary
    >
      <v-list dense>
        <v-list-item link v-for='item in menuItems' :key='item.title' :to='item.link'>
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="teal"
      dark
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" class="hidden-md-and-up" />
      <v-toolbar-title>
        <router-link to='/' tag="span" style="cursor: pointer">DevMeetup</router-link>
        </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-btn text v-for='item in menuItems' :key='item.title' :to='item.link'>
          <v-icon left>{{ item.icon }}</v-icon> {{ item.title }}
        </v-btn>
      </v-toolbar-items>
    </v-app-bar>

    <v-content>
      <router-view></router-view>
    </v-content>

  </v-app>
</template>

<script>
export default {
  name: 'App',
  components: {},

  data: () => ({
    drawer: null,
    menuItems: [
      { icon: 'mdi-account-group', title: 'View Meetups', link: '/meetups' },
      { icon: 'mdi-map-marker', title: 'Organize Meetup', link: '/meetup/new' },
      { icon: 'mdi-account', title: 'Profile', link: '/profile' },
      { icon: 'mdi-face', title: 'Sign Up', link: '/signup' },
      { icon: 'mdi-lock-open', title: 'Sign In', link: '/signin' }
    ]
  })
}
</script>
