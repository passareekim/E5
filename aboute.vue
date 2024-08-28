<template>
    <v-container>
      <v-row>
        <v-col cols="12" md="8" class="mx-auto">
          <v-card class="elevation-3">
            <!-- Card Image -->
            <v-img
              src="\xampp\htdocs\api_e5\app_e5\img\50049.jpg"
              height="200px"
              alt="Banner Image"
            ></v-img>
            
            <!-- Card Title -->
            <v-card-title class="align-center">
              <v-icon class="mr-2" size="40" color="primary">mdi-information-outline</v-icon>
              <span class="text-h5 font-weight-bold">About Us</span>
            </v-card-title>
  
            <!-- Card Subtitle -->
            <v-card-subtitle class="subtitle-1 mb-4 d-flex align-center">
              <v-avatar size="50" class="mr-3">
                <v-img src="C:\xampp\htdocs\api_e5\app_e5\img\50300.jpg" alt="Logo"></v-img>
              </v-avatar>
              Learn more about our team and mission.
            </v-card-subtitle>
  
            <!-- Card Content -->
            <v-card-text>
              <p>
                Welcome to our application! We are dedicated to providing the best
                services and experiences for our users. Our team is passionate about
                delivering high-quality products and customer support.
              </p>
              <p>
                Our mission is to innovate and bring new solutions to the market,
                helping our users achieve their goals with ease.
              </p>
            </v-card-text>
  
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    methods: {
      goBack() {
        this.$router.go(-1); // Navigate back to the previous page
      }
    }
  }
  </script>
  
  <style scoped>
  .v-card-title {
    background-color: #f0f4f8;
    padding: 16px;
  }
  
  .v-card-subtitle {
    color: #607d8b;
  }
  
  .v-card-text p {
    font-size: 16px;
    line-height: 1.6;
    margin-bottom: 16px;
  }
  
  .v-btn {
    font-weight: bold;
  }
  
  .v-img {
    border-radius: 8px;
  }
  </style>
  