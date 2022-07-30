<template>
  <v-app>
    <NavigationBar 
      :internalLinks="internalLinks" 
      :externalLinks="externalLinks" 
      :logo="logo" 
    />
    <v-main>
      <Home />
      <About />
      <Contact 
        v-on:add-user="addUser"
      />
      <DialogBox v-if="displayDialog"  
        :dialogHeader="dialogHeader" 
        :dialogHeaderIcon="dialogHeaderIcon" 
        :dialogText="dialogText"
      />
    </v-main>
    <FooterBar 
      :footerIcons="footerIcons" 
      :footerText="footerText"
      />
  </v-app>
</template>


<script>
import NavigationBar from './components/NavigationBar';
import Home from './components/Home';
import About from './components/About'
import Contact from './components/Contact';
import FooterBar from './components/FooterBar';
import DialogBox from './components/DialogBox'

import { db } from './db'

export default {
  name: 'App',

  components: {
    NavigationBar,
    Home,
    About,
    Contact,
    DialogBox,
    FooterBar

  },

  data() {
    return{
      users: [],
      timestamp : '',
      displayDialog: false,
      dialogHeader: '',
      dialogHeaderIcon: 'mdi-hand-wave-outline',
      dialogText: '',

      logo:"consilium_logo.png",
      internalLinks: [
        {icon: "mdi-home-outline", name: "Home", link: "#home"},
        {icon: "mdi-help", name: "About", link: "#about"},
        {icon: "mdi-email-outline", name: "Contact", link: "#contact"},
      ],
      externalLinks: [
        {icon: "mdi-instagram", name: "Instagram", link: "https://instagram.com/consilium_design_studio"},
      ],
      footerIcons : [
        {
          icon_type: "mdi-facebook",
          link: "https://www.facebook.com/Consilium-Interiors-114152513845625"
        },
        {
          icon_type: "mdi-instagram",
          link: "https://instagram.com/consilium_design_studio",
        },
      ],
      footerText : "Consilium Inc."
    }
  },
  firestore: {
    return: {
      users: db.collection('users'),

    }
  },
  methods: {
    addUser(newUser){
      console.log('Invoked addUser with', newUser);
      db.collection('users').add(newUser)
      .then((docRef) => {
        console.log('User successfully written at : ',docRef);
        this.displayDialog = true;
        this.dialogHeader = 'Hi ' + newUser.name;
        this.dialogText = 'Your request for a free consultation is being processed. We will reach out to you shortly.'
      })
      .catch(
        (error) => {
          console.error('Error: ', error)
        }
      )
  },

  }
};
</script>
