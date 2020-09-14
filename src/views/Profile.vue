<template>
    <div class="profile">
        <v-card elevation="0" class="card pa-5">
            <v-card-text>
                <v-row>
                    <h1 class="card-title">Profile</h1>
                </v-row>
                <v-row class="mb-8">
                    <span class="card-subtitle pb-0">
                        Add your personal information so we can find hosts that look more like you.
                    </span> <br>
                    <span class="card-subtitle py-0">
                        <b>Public info: Native language, Languages, First Name, Picture, Nationality, 
                        Date Of Birth and Country.</b>
                    </span>
                </v-row>
                <v-card outlined class="px-3 pt-3 internal-card">
                    <v-card-text>
                        <v-row class="px-3 mb-2">
                            <h1 class="montserrat blue-font font-weight-light" style="font-size:16;">
                                Personal Informations</h1>
                        </v-row>
                        <v-row class="px-3">
                            <v-col class="ma-0" cols="2">
                                <v-row justify="center">
                                    <v-btn color="primary" class="page-btn" x-small text>Edit Picture</v-btn>
                                </v-row>
                                <v-row justify="center">
                                    <v-avatar size="70">
                                        <img src="https://cdn.vuetifyjs.com/images/john.jpg" alt="John">
                                    </v-avatar>
                                </v-row>
                                <v-row justify="center">
                                    <v-rating dense readonly x-small v-model="rating"></v-rating>
                                </v-row>
                            </v-col>
                            <v-col class="ma-0 pr-0" cols="3">
                                <v-text-field
                                    v-model="first" class="text-field"
                                    label="First Name"   
                                ></v-text-field>
                            <v-menu
                                    ref="menu" 
                                    v-model="menu"  
                                    :close-on-content-click="false"
                                    transition="scale-transition"
                                    min-width="290px"
                                >
                                    <template v-slot:activator="{ on }">
                                    <v-text-field  
                                        v-model="dateFormatted" hint="MM/DD/YYYY" 
                                        label="Birth"  
                                        class="text-field"
                                        v-on="on" 
                                    ></v-text-field>
                                    </template>
                                    <v-date-picker no-title=""
                                    ref="picker" locale="en"  
                                    v-model="date" @blur="date = parseDate(dateFormatted)"
                                    max="2010-01-01"
                                    min="1950-01-01" 
                                    ></v-date-picker>
                                </v-menu>
                            </v-col>
                            <v-col class="mx-0 mb-0 pr-0" cols="3">
                                <v-text-field
                                    v-model="first" class="text-field"
                                    label="Last Name"   
                                ></v-text-field>
                                <v-text-field
                                    color="#000000"
                                    v-model="first" class="text-field"
                                    label="E-mail"   
                                ></v-text-field>
                            </v-col>
                            <v-col cols="3">
                                <v-text-field
                                    
                                    v-model="first" class="text-field"
                                    label="Nacionality"   
                                ></v-text-field>
                                <v-text-field
                                    
                                    v-model="first" class="text-field"
                                    label="Gender"   
                                ></v-text-field>
                            </v-col>
                        </v-row> 
                   </v-card-text>
                </v-card>
            </v-card-text>
            <div v-html="text"></div>
            <v-card-actions class="py-0">
                <v-spacer></v-spacer>
                <v-btn class="page-btn" text>Cancel</v-btn>
                <v-btn class="page-btn" text color="primary">Submit</v-btn>
            </v-card-actions>
        </v-card>
    </div>
</template>

<script>
import MainCard from './../components/MainCard.vue'

export default {
    name: 'Profile',
    components: {
        MainCard
    },
    date: () => ({
        date: null,
        dateFormatted: null,
        minDate: '1920-01-01',
        maxDate: '2010-01-01',
    }),
    watch: {
        date() {
            this.dateFormatted = this.formatDate(this.date)
            //console.log(this.date)
            this.menu = false
        },
    },
    methods: {
        formatDate(date) {
            if (!date) return null

            const [year, month, day] = date.split('-')
            return `${month}/${day}/${year}`
        },
        parseDate(date) {
            if (!date) return null

            const [day, month, year] = date.split('/')
            return `${year}-${month.padStart(2, '0')}-${day.padStart(2, '0')}`
        },
    }
}
</script>

<style>
  .montserrat{
    font-family: 'Montserrat', sans-serif;
  }
  .page-btn{
    letter-spacing: 0px !important;
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
    border: 1px solid #223254 !important;
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
    font-weight: 800;
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
  .text-field{
    font-weight: 800 !important;
    font-family: 'Montserrat', sans-serif;
    font-size: 12px !important;
    font-weight: 200;
    color: #223254 !important;
  }
</style>

