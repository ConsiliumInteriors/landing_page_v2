<template>
  <div>
    <v-navigation-drawer v-model="drawer" app temporary>
      <v-list>
        <v-list-item two-line>
          <v-list-item-content>
            <v-list-item-title>
              <v-img :src="require(`@/assets/consilium_logo.png`)"></v-img>
            </v-list-item-title>
          </v-list-item-content>

        </v-list-item>
      </v-list>
    <v-divider />
      <v-list dense>
        <v-list-item
          v-for="(nav,i) in this.internalLinks"
          :key="i"
          link
          @click="$vuetify.goTo(nav.link)"
        >
          <v-list-item-icon  class="justify-center">
            <v-icon >{{ nav.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title class="subtitile-1">{{
              nav.name
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item
          v-for="(nav) in this.externalLinks"
          :key="nav.name"
          link
          :href="nav.link"
        >
          <v-list-item-icon  class="justify-center">
            <v-icon >{{ nav.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title class="subtitile-1">{{
              nav.name
            }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

    </v-navigation-drawer>

    <v-app-bar app class="px-5">
      <v-toolbar-title class="mb-2">
          <v-img :src="require(`@/assets/${this.logo}`)" alt="Logo" max-width="200px" />
      </v-toolbar-title>
      <v-spacer></v-spacer>

      <v-app-bar-nav-icon
        @click.stop="drawer = !drawer"
        class="mr-4"
        v-if="isXs"
      />
        <div v-if="!isXs">
            <v-btn v-for="(nav) in this.internalLinks" v-bind:key="nav.name" color="black" text @click="$vuetify.goTo(nav.link)">
              <v-icon>{{nav.icon}}</v-icon>
              <span class="mt-1 ml-1 mr-2">{{nav.name}}</span>
            </v-btn>
          <v-btn v-for="(nav) in this.externalLinks" v-bind:key="nav.name" color="black" text :href="nav.link">
            <v-icon>{{nav.icon}}</v-icon>
            <span class="mt-1 ml-1 mr-2">{{nav.name}}</span>
          </v-btn>
        </div> 
    </v-app-bar>
  </div>
</template>


<script>
export default {
  data () {
    return {
    drawer: null,
    isXs: false,
    }
  },
  props: {
    logo: String,
    internalLinks: Array,
    externalLinks: Array,
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
      console.log(this.isXs);
      if (!value) {
        if (this.drawer) {
          console.log('Drawer will be hidden.')
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