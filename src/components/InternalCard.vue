<template>
  <v-app id="sandbox">
    <v-card outlined class="internal-card px-2">
        <v-card-text>
            <v-row>
                <span class="montserrat blue-font font-weight-medium">{{title}}</span>
            </v-row>
            <v-col cols="3">
            </v-col>
            <v-col cols="3">

            </v-col>
            <v-col cols="3">

            </v-col>
            <v-col cols="3">

            </v-col>
        </v-card-text>
    </v-card>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  props: {
    title: String,
  },
  components: {
  },
  data: () => ({
      drawers: ['Default (no property)', 'Permanent', 'Temporary'],
      pages: [
        {name: 'Profile', icon: "mdi-face"}, 
        {name: 'Preferences', icon: "mdi-gamepad-variant-outline"}, 
        {name: 'Host', icon: "mdi-human-greeting"}, 
        {name: 'Travel', icon: "mdi-wallet-travel"}
      ],
      primaryDrawer: {
        model: null,
      },
      footer: {
        inset: false,
      },
    }),
};
</script>

<style>
  .montserrat{
    font-family: 'Montserrat', sans-serif;
  }
  .page-btn{
    letter-spacing: 0px !important;
    text-transform: none !important;
    font-family: 'Montserrat', sans-serif;
    font-weight: 700 !important;
  }
  .card{
    border-radius: 25px !important;
  }
  .internal-card{
    border-radius: 15px !important;
    margin-top: 10px;
  }
  .blue-font{
    color: #223254;
  }
  .foot{
    position: relative !important;
    font-size: 12px;
  }
  .card-title{
    font-size: 45px;
    font-weight: 700;
    font-family: 'Montserrat', sans-serif;
    color: #223254;
    padding-bottom: 20px;;
  }
  .card-subtitle{
    font-size: 9px;
    font-weight: 500;
    font-family: 'Montserrat', sans-serif;
    color: #969c99;
    padding-left: 4px;
  }
</style>
