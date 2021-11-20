<template>
    <v-container id="gallery" fluid class="pa-8 " >
            <v-row dense>
                 <v-col cols="12"  class="text-center" align-self="center">
                    <!-- <v-divider class="pa-4">
                    </v-divider> -->


                </v-col>
                <v-col cols="12"  class="text-center" align-self="center">
                            <h3 id="title">
                                Gallery
                            </h3>
                </v-col>

                <!-- <v-col cols="12" class="text-center pt-16" align-self="center">
                            <h4 id="subtitle">
                                Choose from collections below. 
                            </h4>
                </v-col> -->
                <v-col cols="12" class="text-center" align-self="center">
                    <Popup />
                </v-col>
            </v-row>




        
        </v-container>

</template>


<script>
import Popup from './Popup';
export default {
    components: {
        Popup,
    },
    data(){
    return {
        items : [

        ],
        sample_items_three : [

        ],

    }
    }

    
}
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Lobster&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Yesteryear&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');
#gallery {
    background-color: white;
}
#title {
    color: black;
    font-size: 2rem;
    letter-spacing: 0.1rem;
    font-family: 'Lobster';
}
#subtitle {
    color: black;
    font-size: 1rem;
    /* letter-spacing: 0.1rem; */
    font-family: 'Lato';
}

</style>>
