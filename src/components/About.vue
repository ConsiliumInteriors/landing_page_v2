<template>
    <div id="about">
    <v-container class="about-container py-16" fluid>
        <v-row align="center" justify="center">
            <v-col cols="12" class="text-center py-4">
                <span>
                <h3 id="title"> 
                    How do I get started..
                    <v-icon color="primary" size="42px" class=" ml-2 mb-4">mdi-chat-question-outline </v-icon>
                </h3> 



                </span>
            </v-col>
            <v-col cols="12" md="3" class="pa-8 text-center" v-for="(step,idx) in steps" v-bind:key="idx">
                <v-icon color="primary" size="32px">
                    {{step.icon}}
                </v-icon>
                <h3 id="content-title" class="pa-2">{{ step.title}}</h3>
                <p class="pa-2" id="content"> {{step.subtitle}}</p>

            </v-col>

        </v-row>
    </v-container>
    <!-- <div id="about-container" class="container-fluid">
    <div class="row p-4">
        <div id="feature-title" class="col-lg-8 offset-lg-2">
        </div>

    </div>
    <div class="row p-4">
        <div class="col-md-3 p-4">
            <i class="fa fa-calendar fa-3x"></i>
            <h3> Contact</h3>
            <p> Click the 'Book now' button and we will reach out to you for a free consultation. 
            </p>
        </div>
        <div class="col-md-3 p-4">
            <i class="fa fa-lightbulb-o fa-3x"></i>
            <h3> Plan</h3>
            <p> Our experts will help you work out your design, delivarables and timelines.
            </p>
        </div>
        <div class="col-md-3 p-4">
            <i class="fa fa-cogs fa-3x"></i>
            <h3> Execute</h3>
            <p> Sit back and relax while we put the plan into action.
            </p>
        </div>
        <div class="col-md-3 p-4">
            <i class="fa fa-home fa-3x"></i>
            <h3 >Move in </h3>
            <p> Move in to your dream home.
            </p>
        </div>
    </div>
</div> -->
    </div>
</template>

<script>
export default {
        data(){
        return {
            steps: [
                {
                    'title':'Contact',
                    'subtitle':'Register below and we will reach out to you for a free consultation. You can also give us a call on the number listed below.',
                    'icon': 'mdi-email-outline'
                },
                {
                    'title':'Plan',
                    'subtitle':'Our experts will help you work out your design, delivarables and timelines.',
                    'icon': 'mdi-lightbulb'
                },
                {
                    'title':'Execute',
                    'subtitle':'Sit back and relax while we put the plan into action. We pride ourselves on delivering on time.',
                    'icon': 'mdi-cogs'
                },
                {
                    'title':'Move in',
                    'subtitle': 'Move in to your dream home. Be sure to give us some feedback as well.',
                    'icon': 'mdi-home-outline'
                }
 
            ]
        }
        }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Lobster&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Yesteryear&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

.about-container {
    background-color: white;
}

#title {
    color: black;
    font-size: 2rem;
    font-family: 'Lato';
}
#content-title {
    color: black;
    font-size: 1.5rem;
    font-family: 'Lato';
}
#content {
    color: black;
    font-size: 1rem;
    font-family: 'Lato';
}
</style>