<template>
  <v-app>
    <v-main>
      <Nuxt />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { Component, Vue } from "nuxt-property-decorator";

@Component({
  filters: {},
})
export default class Default extends Vue {
  [x: string]: any;
}
</script>
