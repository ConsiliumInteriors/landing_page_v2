<template>
  <div class="text-center">
    <v-dialog v-model="dialog" width="500">
      <v-card>
        <v-card-title class="text-h5">
            <v-icon>{{this.dialogHeaderIcon}}</v-icon>
            <span class="ml-2">{{this.dialogHeader}}</span>
        </v-card-title>
        <v-card-text>
            {{this.dialogText}}
        </v-card-text>
        <v-divider></v-divider>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="black" text @click="dialog = false">
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        dialog: true
      }
    },
    props: {
        dialogHeader: {
            type: String
        },
        dialogHeaderIcon: {
            type: String
        },

        dialogText: {
            type: String
        }
    },
        

  }
</script>