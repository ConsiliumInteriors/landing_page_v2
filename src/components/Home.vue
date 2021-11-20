<template>
    <div id="home">
    <v-parallax  src="../assets/heroImages/Hero.jpg" height="750">
        <v-overlay absolute>
            <v-row align="center" justify="center">
                <v-col cols="12" class="text-center">
                    <h3 id="title">{{ heroTitle}} </h3>
                    <p id="subtitle">{{ heroSubtitle }}</p>
                </v-col>
            </v-row>
        </v-overlay>
    </v-parallax>
    </div>
</template>

<script>
export default {
    components: {
    },
    data() {
        return {
            heroTitle : 'Consilium Interiors',
            heroSubtitle: '"We make room for what is important to you."'
        }
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Lobster&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Yesteryear&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

/* .v-parallax__image {
      background: 
    linear-gradient(
      rgba(129, 95, 95, 0), 
      rgba(1, 1, 1, 0)
    ),
    url('../assets/hero_one.jpg')!important;  
} */

#title {
    color:white;
    margin: 0;
    font-size: 4rem;
    font-weight:900;
    letter-spacing: 0.1rem;
    font-family: 'Lobster';
}

#subtitle {
    font-family: 'Lato';
    color: #fff;
    margin: 0;
    font-size: 1.5rem;
    font-weight: 900;
    letter-spacing: 0.1rem;
}

#subtitle-small {
    color:black;
    margin: 0;
    font-size: 1rem;
    font-weight: 400;
}

</style>