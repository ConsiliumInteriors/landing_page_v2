<template>
  <div>
    <v-navigation-drawer
      v-model="drawer"
      app
      temporary
    >
      <v-list>
        <v-list-item two-line> 
          <v-list-item-content>
            <v-list-item-title 
            class="title"
            >
            <v-img
              src="@/assets/consilium_logo.png" alt="Logo"
            ></v-img>
            </v-list-item-title>

          </v-list-item-content>
        </v-list-item>
       
      </v-list>

      <v-divider />

      <v-list dense>
        <v-list-item
          v-for="([icon, text, link], i) in items"
          :key="i"
          link
          @click="$vuetify.goTo(link)"
        >
          <v-list-item-icon class="justify-center">
            <v-icon>{{ icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title class="subtitile-1">{{
              text
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

    </v-navigation-drawer>

    <v-app-bar
      app
      color="white"      
      class="px-5"
      elevation="0"
    >
      <v-toolbar-title class="mb-2">
          <v-img src="@/assets/consilium_logo.png" max-width="200px" />
      </v-toolbar-title>

      <v-spacer />

      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
        class="mr-4"
        v-if="isXs"
      />
      <div v-else>
        <v-btn color="black" text @click="$vuetify.goTo('#home')">
            <v-icon>
              mdi-home-outline
            </v-icon>
          <span class="mt-1 ml-1 mr-2">
            Home
          </span>
        </v-btn>
        <v-btn  color="black" text @click="$vuetify.goTo('#about')">
            <v-icon>
              mdi-help-circle-outline
            </v-icon>
          <span class="mt-1 ml-1 mr-2">About</span>
        </v-btn>
        <v-btn  color="black" text @click="$vuetify.goTo('#contact')">
          <v-icon>
            mdi-email-outline
          </v-icon>
          <span class="mt-1 ml-1 mr-2">Contact</span>
        </v-btn>
      </div>
    </v-app-bar>
  </div>
</template>

<style scoped>
.v-toolbar {
  transition: 0.6s;
}

.expand {
  height: 80px !important;
  padding-top: 10px;
}


</style>

<script>

export default {
  data: () => ({
    drawer: null,
    isXs: false,
    navigation_items: [
      {
        "icon":"mdi-home-outline",
        "title":"Home",
        "link":"#home"
      },
      {
        "icon":"mdi-help",
        "title":"About",
        "link":"#about"
      },{},{}
    ],
    items: [
      ["mdi-home-outline", "Home", "#home"],
      ["mdi-instagram", "Gallery", "#gallery"],
      ["mdi-help", "About", "#about"],
      ["mdi-email-outline", "Contact", "#contact"],
    ],
  }),

  props: {
    color: String,
    flat: Boolean,
  },

  methods: {
    onResize() {
      this.isXs = window.innerWidth < 850;
    },
  },

  watch: {
    isXs(value) {
      if (!value) {
        if (this.drawer) {
          this.drawer = false;
        }
      }
    },
  },
  mounted() {
    this.onResize();
    window.addEventListener("resize", this.onResize, { passive: true });
  },

};
</script>