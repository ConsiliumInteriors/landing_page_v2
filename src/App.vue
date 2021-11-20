<template>
  <v-app>
    <Navigation />
    <v-main>
      <Home />
      <!-- <Products /> -->
      <About />
      <!-- <ProductCards /> -->
      <Contact v-on:add-user="addUser"/>
    </v-main>
    <Footer />


  </v-app>
</template>

<script>
import Navigation from './components/Navigation';
import Home from './components/Home';
// import Products from './components/Products';
import About from './components/About'
// import ProductCards from './components/ProductCards';
import Contact from './components/Contact';
import Footer from './components/Footer';

import { db } from './db'

export default {
  name: 'App',

  components: {
    Navigation,
    Home,
    // Products,
    About,
    // ProductCards,
    Contact,
    Footer

  },

  data: () => ({
    return:{
      users: [],
      timestamp : ''

    }
  }),

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

<style>


</style>
