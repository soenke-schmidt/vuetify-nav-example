<template>
  <v-list-item
    v-if="!subNavigationGroups"
    :nuxt="!!to"
    :to="to"
    :href="href"
  >
    <v-list-item-content>
      <v-list-item-title>{{ text }}</v-list-item-title>
    </v-list-item-content>
  </v-list-item>
  <v-list-group v-else>
    <template #activator>
      <v-list-item-content>
        <v-list-item-title>{{ text }}</v-list-item-title>
      </v-list-item-content>
    </template>
    <v-list-item-group
      v-for="(subNavigationGroup, sngIndex) in subNavigationGroups"
      :key="`sng-${sngIndex}`"
    >
      <v-subheader v-if="subNavigationGroup.text">
        {{ subNavigationGroup.text }}
      </v-subheader>
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
            {{ subNavgitationItem.text }}
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list-item-group>
  </v-list-group>
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
  }
}
</script>

<style>
</style>
