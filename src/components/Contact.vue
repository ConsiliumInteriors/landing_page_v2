<template>
    <v-container  id="contact" class="image-background" fluid>
        <v-row dense>
            <v-col cols="12" >
                <v-col cols="12" class="text-center">
                    <h3 id="hero-title"> Get in touch...</h3>
                </v-col>

            </v-col>

            <v-col cols="12">
                <v-container fluid class="pa-0 ma-0">
                    <!-- <v-img src="../assets/arch3.jpg"   max-height="600" gradient="45deg, rgba(1,1,1,1), rgba(1,1,1,0.6)"> -->
                <v-row justify="space-around">
                    <v-col cols="12" md="4">
                            <div id="address_card_container">
                                <v-card color="rgb(1,1,1,0)"  flat>
                                    <div id="contact-component" v-for="(item,i) in addressContent" v-bind:key="i">
                                        <v-icon id="contact-component-icon" color="white"> {{ item.icon}}</v-icon>
                                        <h3 id="contact-component-title">{{ item.title}}</h3>
                                        <h3 id="contact-component-subtitle">{{item.content}}</h3>
                                    </div>
                                </v-card>
                            </div>

                    </v-col>
                    <v-col cols="12" md="4">
                         <div id="contact_card_container">
                            <v-card dark color="rgb(1,1,1,0)" flat>
                                <div id="contact-component">
                                    <v-form  v-model="valid" v-on:submit.prevent="submitForm"  ref="form">
                                        <v-row dense  align="center" justify="center">
                                            <v-col cols="12" class="text-center">
                                                <v-text-field  id="form-field-name"  label="Name"  prepend-icon="mdi-account" dense v-model="name" :rules="nameRules"></v-text-field>
                                            </v-col>
                                            <v-col cols="12">
                                                <v-text-field  id="form-field-email"  label="Email" prepend-icon="mdi-email"  dense v-model="email" :rules="emailRules">
                                                </v-text-field>
                                            </v-col>
                                            <v-col cols="12">
                                                <v-select id="form-field-location" label="Location" prepend-icon="mdi-domain" dense v-model="location" :items="cities"  :rules="locationRules">
                                                </v-select>
                                            </v-col>
                                            <v-col cols="12" class="text-center">
                                                <v-btn @click="submitForm" color="rgb(218,165,32)">
                                                    Get a Free Quote
                                                </v-btn>
                                            </v-col>
                                        </v-row>

                                    </v-form>

                                </div>
                            </v-card>
                        </div>



                    </v-col>

                    <!-- <v-col cols="12" md="4">
                            <div id="logo_container">
                                <v-card color="rgb(1,1,1,0)"  flat>
                                    <div id="logo-component">
                                        <v-img src="../assets/consilium_logo_white.png">

                                        </v-img>

                                    </div>
                                </v-card>
                            </div>

                    </v-col> -->

                    

                </v-row>












                    <!-- </v-img> -->

                </v-container>

                
            </v-col>
        </v-row>
    </v-container>


    
                        <!-- <v-col cols="12" class="text-center" align-self="center">
                            <v-row>
                                <v-col cols="12">
                                    <h3 id="title"> Get in touch </h3>
                                </v-col>
                            </v-row>
                        </v-col>

                        <v-col cols="6">
                            <v-row  justify="space-around">
                                <v-col cols="12">
                                    <v-row>
                                        <v-col cols="12" md="6" class="text-center">
                                                Address
                                        </v-col>
                                    <v-col cols="12" md="6" lg="6">
                                                Register

                                            <v-form v-model="valid" v-on:submit.prevent="submitForm" lazy-validation ref="form">
                                                <v-row dense  align="center" justify="center" class="mt-16">
                                                    <v-col cols="12">
                                                        <v-text-field  id="form-field-name"  label="Name" dense  v-model="name" :rules="nameRules"></v-text-field>
                                                    </v-col>
                                                <v-col cols="12">
                                                    <v-text-field  id="form-field-email"  label="Email" dense   v-model="email" :rules="emailRules">
                                                    </v-text-field>
                                                </v-col>
                                                <v-col cols="12">
                                                    <v-select id="form-field-location" label="Location"  filled  dense v-model="location" :items="cities"  :rules="locationRules">
                                                    </v-select>
                                                </v-col>
                                                <v-col cols="8" offset="4">
                                                    <v-btn @click="submitForm">
                                                        SUBMIT 
                                                    </v-btn>
                                                </v-col>
                                                </v-row>

                                            </v-form>

                                    </v-col>
                                </v-row>
                            </v-col>
                        </v-row>
                    </v-col> -->
</template>



<script>

export default {
    name: "Contact",
    data() {
      return {
        valid: false,
        name: '',
        nameRules: [
        v => !!v || 'Name is required',
        v => (v && v.length <= 25)|| 'Name must be less than 25 characters',
        ],
        email: '',
        emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid',
        ],
        location: '',
        locationRules : [
            v => !!v || 'Location is required.',
        ],
        hasSubmitted: false,
        cities : ['Kochi'],
        addressContent : [
            {
                'title':'Address',
                'content':'Crescens Towers L9, Level IV, NH-47, Kalamassery, Kochi',
                'icon':'mdi-domain'
            },
            {
                'title':'Call us/ Chat',
                'content':'+91 7907751388',
                'icon':'mdi-whatsapp'
            },
            {
                'title':'General Support',
                'content':'contact@consiliuminteriors.com',
                'icon':'mdi-email'
            }
        ],

      }
    },
    methods: {
      submitForm() {
        this.valid = this.$refs.form.validate();
        this.timestamp = this.getNow();
        if (this.valid) {
            const newUser = {
                email: this.email,
                name: this.name,
                location: this.location,
                createdAt : this.timestamp,
                modifiedAt: this.timestamp,
                status: 'created'
            }
            this.$emit('add-user', newUser);
            this.$refs.form.reset();
            this.hasSubmitted = true;
            setTimeout(function () { 
                this.hasSubmitted = false; 
            }, 2000);
        }
        else {
            console.log('Form validation failed.')
        }
      },
      resetForm() {
        console.log('resetForm invoked.'); 

        this.hasSubmitted = false;

      },
    getNow : function() {
        const today= new Date();
        const date = today.getFullYear()+'-'+(today.getMonth()+1)+'-'+today.getDate();
        const time = today.getHours() + ":" + today.getMinutes() + ":" + today.getSeconds();
        const dateTime = date +'T'+ time;
        return dateTime;
  }

    }
}
</script>


<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Lobster&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

.white-background {
    background-color:whitesmoke;
}

.image-background {
    background: 
    /* top, transparent red, faked with gradient */ 
    linear-gradient(
      rgba(1, 1, 1, 0.8), 
      rgba(1, 1, 1, 0.8)
    ),
    /* bottom, image */
    url('../assets/chair-cgi2.jpg');

}
#hero-title {
    color:white;
    font-size: 2rem;
    font-family: 'Lobster';
    letter-spacing: 0.1rem;
}

#contact-component{
    margin-top:2rem;

}

#contact-component-icon {
    margin-right: 1rem;
    float: left;
}

#contact-component-title {
    color: white;
    font-size: 1rem;
    font-family: 'Lato';
    font-weight: 100;
    /* font-family: 'Lobster'; */
    /* letter-spacing: 0.1rem; */
}

#contact-component-subtitle {
    color: goldenrod;
    font-size: 0.9rem;
    font-family: 'Lato';
    font-weight: 200;
    margin-left: 2rem;
    /* font-family: 'Lobster'; */
    /* letter-spacing: 0.1rem; */
}


#form-field-name {
    font-size: 2rem!important;
}

.contact-form-outer {
    background-color: white;
}

</style>