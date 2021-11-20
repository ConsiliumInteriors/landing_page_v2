<template>
<v-container>
  <v-row>
    <v-col cols="12" md="6" v-for="(collection,i) in collections" v-bind:key="i">
      <v-dialog max-width="70%">
        <template v-slot:activator="{ on, attrs }">
            <v-card dark> 
                  <v-img :src="collection.thumbnail" gradient="to top right, rgba(1,1,1,0), rgba(1,1,1,0)" class="align-center">

                    <v-card-actions class="justify-center"> 
                        <v-btn color="primary" v-bind="attrs" v-on="on">
                          <!-- <v-icon size="32px">
                          mdi-instagram

                          </v-icon> -->
                          {{ collection.title }}

                        </v-btn>
                      
                    </v-card-actions>  


                </v-img>

            </v-card>
        </template>
    

        <template v-slot:default="dialog">
          <v-card>  

            <v-toolbar light> #{{ collection.title }} </v-toolbar>

            <v-card-text>
                <v-carousel height="auto" dark>  
                    <v-carousel-item v-for="(image,i) in collection.images" :key="i" :src="image">
                    </v-carousel-item>
                </v-carousel>
            </v-card-text>
            <v-card-actions class="justify-end">
              <v-btn color="primary"  @click="dialog.value = false">Close</v-btn>
            </v-card-actions>
          </v-card>
        </template>
      </v-dialog>
    </v-col>


  </v-row>
</v-container>

</template>
<script>
export default {
    data(){
        return {
            collections: [
                {
                    'title':'Greyscale Grandeur',
                    'thumbnail':require('../assets/galleryImages/greyscaleGrandeur/LivingRoom01.png'),
                    'images': [
                        require('../assets/galleryImages/greyscaleGrandeur/LivingRoom01.png'),
                        require('../assets/galleryImages/greyscaleGrandeur/LivingRoom02.png'),
                        require('../assets/galleryImages/greyscaleGrandeur/Kitchen01.png'),
                        require('../assets/galleryImages/greyscaleGrandeur/DiningRoom01.png'),
                        require('../assets/galleryImages/greyscaleGrandeur/KitchenDining01.png'),
                        require('../assets/galleryImages/greyscaleGrandeur/Bedroom01.png'),
                        require('../assets/galleryImages/greyscaleGrandeur/Bedroom02.png'),
                        require('../assets/galleryImages/greyscaleGrandeur/Bathroom01.png'),
                        require('../assets/galleryImages/greyscaleGrandeur/Bathroom02.png'),
                    ]
                },
                {
                    'title':'Collection #2',
                    'thumbnail':require('../assets/sample01.jpg'),
                    'images': [
                        require('../assets/sample05.jpg'),
                        require('../assets/sample06.jpg')


                    ]
                },
                {
                    'title':'Collection #2',
                    'thumbnail':require('../assets/gg-4.png'),
                    'images': [
                        require('../assets/sample05.jpg'),
                        require('../assets/sample06.jpg')


                    ]
                },
                {
                    'title':'Collection #2',
                    'thumbnail':require('../assets/gg-3.png'),
                    'images': [
                        require('../assets/sample05.jpg'),
                        require('../assets/sample06.jpg')


                    ]
                },
            ]
        }
    }
}

</script>

<style scoped>

</style>