<template>
  <v-app id="sandbox">
    <v-card class="card pa-5">
        <v-card-title>
        <v-row>
            <h1 class="card-title">{{title}}</h1>
        </v-row>
        <v-row class="py-0">
            <span v-html="subtitle" class="card-subtitle pb-0"></span>
            <span v-html="description" class="card-subtitle"></span>
        </v-row>
        </v-card-title>
        <div v-html="text"></div>
        <v-card-actions class="py-0">
        <v-spacer></v-spacer>
        <v-btn class="page-btn" text>Cancel</v-btn>
        <v-btn class="page-btn" text color="primary">Submit</v-btn>
        </v-card-actions>
    </v-card>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  props: {
    source: String,
    title: String,
    subtitle: String,
    description: String, 
    text: String
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
