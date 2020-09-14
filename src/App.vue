<template>
  <v-app>
    <v-navigation-drawer v-model="primaryDrawer.model" temporary floating
      app height="95%"  class="mt-15 pt-5 pl-3" style="border-top-right-radius: 15px;"
       color="#25efc8"
    >
      <v-row class="pt-5 px-5" v-for="i in pages" :key="i">
        <v-btn rounded class="blue-font page-btn" text>
          <v-icon left>{{i.icon}}</v-icon> {{i.name}}
        </v-btn>
      </v-row>
    </v-navigation-drawer>

    <v-app-bar color="#1d5dff" height="80px" dark style="border-bottom-right-radius: 15px;"
      app
    >
      <v-app-bar-nav-icon
        v-if="primaryDrawer.type !== 'permanent'"
        @click.stop="primaryDrawer.model = !primaryDrawer.model"
      ></v-app-bar-nav-icon>
      <v-toolbar-title class="font-weight-bold pa-0 montserrat">Be Cullen</v-toolbar-title>
    </v-app-bar>

    <v-main class="app-bg">
      <v-container fluid>
        <v-row
          align="center"
          justify="center"
        >
          <v-col cols="10">
            <v-row class="my-10" align="center" justify="center">
                <v-btn :rounded="i.name === currentRoute ? 'true' : 'false'"  :text="i.name === currentRoute ? 'true' : 'false'"
                color="#ffc628" class="mx-5 page-btn" v-for="i in pages" :key="i.name" cols="2"> 
                    {{i.name}}
                </v-btn>
            </v-row>
            <router-view></router-view>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
    
    <v-footer :inset="footer.inset">
      <span class="px-4 montserrat foot font-weight-bold blue-font"> Be Cullen &copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
import MainCard from './components/MainCard.vue'

export default {
  name: 'App',
  props: {
    source: String,
  },
  components: {
    MainCard
  },
  created() {
    console.log(this.currentRoute)
  },
  data: () => ({
    currentRoute: window.location.pathname,
    drawers: ['Default (no property)', 'Permanent', 'Temporary'],
    pages: [
      {name: 'profile', icon: "mdi-face"}, 
      {name: 'preferences', icon: "mdi-gamepad-variant-outline"}, 
      {name: 'host', icon: "mdi-human-greeting"}, 
      {name: 'travel', icon: "mdi-wallet-travel"}
    ],
    primaryDrawer: {
      model: null,
    },
    footer: {
      inset: false,
    },
  }),
  methods: {
    validateBtnColor(btn, atribute) {
        if(btn.name === currentRoute) {
          
        }
    }
  }
}
</script>

<style>
  .app-bg{
    background-color: #f2f3f3;
  }
  .montserrat{
    font-family: 'Montserrat', sans-serif;
  }
  .page-btn{
    letter-spacing: 0px !important;
    text-transform: none !important;
    text-transform: capitalize !important;
    font-family: 'Montserrat', sans-serif;
    font-weight: 700 !important;
    box-shadow: none !important;
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
    padding-bottom: 20px;
  }
  .card-subtitle{
    font-size: 9px;
    font-weight: 500;
    font-family: 'Montserrat', sans-serif;
    color: #969c99;
    padding-left: 4px;
  }
</style>
