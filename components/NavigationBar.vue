<template>
  <nav>
    <v-app-bar app fixed clipped-left>
      <v-container class="pa-0 fill-height">
        <NuxtLink to="/" title="Startseite">
          <v-img
            max-height="130"
            max-width="130"
            :src="require('~/assets/img/fast-banana.svg')"
          />
        </NuxtLink>

        <v-spacer />
        <template v-if="$vuetify.breakpoint.mdAndUp">
          <HorizontalNavigationItem
            v-for="(navigationItem, index) in navigationItems"
            v-bind="navigationItem"
            :key="`navigation-item-${index}`"
          />
        </template>
        <v-spacer />
        <v-app-bar-nav-icon v-if="true" @click.stop="drawer = !drawer" />
      </v-container>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" app clipped>
      <p class="font-italic pt-8">
        TODO: Implement!
      </p>
    </v-navigation-drawer>
  </nav>
</template>

<script>
import HorizontalNavigationItem from './HorizontalNavigationItem.vue'
export default {
  components: { HorizontalNavigationItem },
  data: () => ({
    drawer: false,
    navigationItems: [
      {
        text: 'Inspire',
        to: '/inspire'
      },
      {
        text: 'External',
        href: 'https://www.example.com'
      },
      {
        text: 'Menu',
        subNavigationGroups: [
          {
            text: 'Subnavigation Group 1',
            subNavigationItems: [
              {
                text: 'External 1',
                href: 'https://www.example.com'
              },
              {
                text: 'External 2',
                href: 'https://www.example.com'
              }
            ]
          },
          {
            text: 'Subnavigation Group 2',
            subNavigationItems: [
              {
                text: 'Inspire',
                to: '/inspire'
              }
            ]
          },
          {
            text: 'Subnavigation Group 3',
            subNavigationItems: [
              {
                text: 'Home',
                to: '/'
              }
            ]
          },
          {
            text: 'Subnavigation Group 4',
            subNavigationItems: [
              {
                text: 'External 3',
                to: '/i-do-not-exist'
              }
            ]
          }

        ]
      },
      {
        text: 'Menu 2',
        subNavigationGroups: [{
          // text: 'No Text for this group',
          subNavigationItems: [
            {
              text: '404',
              to: '/i-do-not-exist'
            },
            {
              text: '404',
              to: '/i-do-not-exist'
            }
          ]
        }]
      }
    ]
  })
}
</script>

<style>
</style>
