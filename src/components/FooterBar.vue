<template>
  <v-footer padless dark>
    <v-card flat tile class="white--text text-center" dark color="black">
      <v-divider></v-divider>
      <v-card-text class="">
        <v-btn
          v-for="(icon, i) in this.footerIcons"
          :key="i"
          class="mx-4 white--text"
          :href="icon.link"
          target="_blank"
          icon
        >
          <v-icon size="24px">{{ icon.icon_type }}</v-icon>
        </v-btn>
      </v-card-text>
      <v-divider></v-divider>
      <v-card-text class="white--text">
        {{ new Date().getFullYear() }} — <strong>{{this.footerText}}</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<style scoped>
.v-card {
  width: 100%;
}
</style>

<script>
export default {
  data () {
    return {

    }
  },
  props: {
    footerIcons: {
      type: Array
    },

    footerText: {
      type: String
    }
  
  }
  
  
};
</script>
