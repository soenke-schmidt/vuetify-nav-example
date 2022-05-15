<template>
  <v-btn v-if="!subNavigationGroups" plain :nuxt="!!to" :to="to" :href="href">
    {{ text }}
  </v-btn>
  <v-menu v-else v-model="menuOpen" offset-y>
    <template #activator="{ on, attrs }">
      <v-btn plain v-bind="attrs" :class="{ active: menuOpen }" v-on="on">
        {{ text }}
        <v-icon>mdi-chevron-down</v-icon>
      </v-btn>
    </template>
    <v-list>
      <v-row dense>
        <v-col
          v-for="(subNavigationGroup, sngIndex) in subNavigationGroups"
          :key="`sng-${sngIndex}`"
          :cols="menuColumns"
        >
          <v-list-item-group :key="`sng-${sngIndex}`">
            <v-subheader>{{ subNavigationGroup.text }}</v-subheader>
            <v-list-item
              v-for="(
                subNavgitationItem, sniIndex
              ) in subNavigationGroup.subNavigationItems"
              :key="`sni-${sngIndex}-${sniIndex}`"
              :nuxt="!!subNavgitationItem.to"
              :to="subNavgitationItem.to"
              :href="subNavgitationItem.href"
            >
              <v-list-item-content>
                <v-list-item-title>
                  {{
                    subNavgitationItem.text
                  }}
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-item-group>
        </v-col>
      </v-row>
    </v-list>
  </v-menu>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      required: true
    },
    to: String,
    href: String,
    subNavigationGroups: Array
  },
  data: () => ({
    menuOpen: false
  }),
  computed: {
    menuColumns () {
      return this.subNavigationGroups && this.subNavigationGroups.length > 2
        ? 4
        : 12 / this.subNavigationGroups.length
    }
  }
}
</script>

<style scoped>
.v-btn.active .v-icon {
  transform: rotate(-180deg);
}
</style>
