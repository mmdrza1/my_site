<template>
  <v-app dark>
    <v-app-bar fixed app flat v-if="$vuetify.breakpoint.mdAndUp">
      <div class="full-width d-flex align-center justify-space-between">
        <div class="half-width d-flex justify-center">
          <v-btn
            class="mr-4"
            v-for="(item, index) in socialMedia"
            :key="index"
            :color="item.color"
            icon
            large
            ><v-icon>{{ item.icon }}</v-icon></v-btn
          >
        </div>
        <div class="half-width d-flex justify-space-around align-center">
          <div>
            <v-btn
              class="mr-4"
              v-for="(item, index) in pages"
              :key="index"
              @click="route(item.link, index)"
              :class="selectedBtn === index ? 'selected-btn' : ''"
              text
              >{{ item.title }}</v-btn
            >
          </div>
          <v-btn dark @click="toggleTheme" icon>
            <v-icon color="yellow" v-if="!$vuetify.theme.dark" x-large
              >mdi-weather-sunny</v-icon
            >
            <v-icon color="blue lighten-1" v-else x-large
              >mdi-moon-waxing-crescent</v-icon
            >
          </v-btn>
        </div>
      </div>
    </v-app-bar>

    <v-app-bar fixed app flat v-else>
      <v-app-bar-nav-icon @click="drawer = true" />
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" absolute temporary>
      <div class="d-flex justify-end pa-4">
        <v-btn dark @click="toggleTheme" icon>
        <v-icon color="yellow" v-if="!$vuetify.theme.dark" x-large
          >mdi-weather-sunny</v-icon
        >
        <v-icon color="blue lighten-1" v-else x-large
          >mdi-moon-waxing-crescent</v-icon
        >
      </v-btn>
      </div>
      
      <div
        class="d-flex flex-column align-center half-height justify-space-around"
      >
        <v-btn
          v-for="(item, index) in pages"
          :key="index"
          @click="route(item.link, index)"
          :class="selectedBtn === index ? 'selected-btn' : ''"
          text
          >{{ item.title }}</v-btn
        >
      </div>
    </v-navigation-drawer>
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

  //* variables
  private drawer: boolean = false;
  private selectedBtn: number = 0;
  private pages = [
    { title: "Home", link: "index" },
    { title: "About", link: "about" },
    { title: "Contact", link: "contact" },
    { title: "Comment", link: "comment" },
  ];
  private socialMedia = [
    { icon: "mdi-twitter", color: "#1DA1F2" },
    { icon: "mdi-instagram", color: "#8a3ab9" },
    { icon: "mdi-whatsapp", color: "#25D366" },
  ];

  //*functionality
  private toggleTheme() {
    this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
    localStorage.setItem("darkMode", this.$vuetify.theme.dark);
  }
  private route(link: string, index: number) {
    this.$router.push({ name: link });
    this.selectedBtn = index;
  }

  //*lifecycle
  created() {
    const theme = localStorage.getItem("darkMode");
    if (theme == "true") {
      this.$vuetify.theme.dark = true;
    } else {
      this.$vuetify.theme.dark = false;
    }
  }
}
</script>
