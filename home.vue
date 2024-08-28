<template>
    <v-app>
      <!-- Main Content -->
      <v-main>
        <v-container>
          <v-row>
            <v-col>
              <h1>ยินดีต้อนรับสู่หน้าหลัก</h1>
              <p>นี่คือเนื้อหาหลักของหน้า "หน้าหลัก"</p>
            </v-col>
          </v-row>
  
          <!-- Row for Image Cards -->
          <v-row>
            <!-- First Image Card -->
            <v-col cols="12" md="6">
              <v-card class="mx-auto my-5" max-width="400">
                <v-img
                  src="\xampp\htdocs\api_e5\app_e5\img/50049.jpg"
                  alt="กีฬาสีปี 2565"
                  height="200px"
                ></v-img>
                <v-card-title>กีฬาสีปี 2565</v-card-title>
                <v-card-subtitle>
                  This is a description of the first image. You can customize this content.
                </v-card-subtitle>
                <v-card-actions>
                  <v-btn color="primary">Learn More</v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
  
            <!-- Second Image Card -->
            <v-col cols="12" md="6">
              <v-card class="mx-auto my-5" max-width="400">
                <v-img
                  src="\xampp\htdocs\api_e5\app_e5\img/50163.jpg"
                  alt="รับน้องปี 2566"
                  height="200px"
                ></v-img>
                <v-card-title>รับน้องปี 2566</v-card-title>
                <v-card-subtitle>
                  This is a description of the second image. You can customize this content.
                </v-card-subtitle>
                <v-card-actions>
                  <v-btn color="primary">Learn More</v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
  
        </v-container>
      </v-main>
    </v-app>
  </template>
  
  <script>
  export default {
    data() {
      return {
        drawer: false,
      };
    },
    methods: {
      goHome() {
        console.log("Navigating to Home");
        // Add your navigation logic here
      },
      goAbout() {
        console.log("Navigating to About");
        // Add your navigation logic here
      },
      goContact() {
        console.log("Navigating to Contact");
        // Add your navigation logic here
      },
    },
  };
  </script>
  
  <style scoped>
  /* Add any custom styles here if needed */
  </style>
  