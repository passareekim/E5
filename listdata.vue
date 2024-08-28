<template>
    <v-app>
      <v-container fluid>
        <!-- Page Title -->
        <v-row>
          <v-col>
            <v-card>
    
              <v-card-text>
                <!-- Data Table -->
                <v-data-table
                  :headers="headers"
                  :items="items"
                  :items-per-page="5"
                  item-key="id"
                >
                  <template v-slot:top>
                    <v-toolbar flat>
                      <v-toolbar-title>ข้อมูลที่แสดง</v-toolbar-title>
                      <v-spacer></v-spacer>
                      <v-btn color="primary" @click="addNewItem">
                        เพิ่มข้อมูล
                      </v-btn>
                    </v-toolbar>
                  </template>
  
                  <template v-slot:item.actions="{ item }">
                    <v-icon small @click="viewDetails(item)">mdi-eye</v-icon>
                    <v-icon small @click="editItem(item)">mdi-pencil</v-icon>
                    <v-icon small @click="deleteItem(item)">mdi-delete</v-icon>
                  </template>
  
                  <template v-slot:no-data>
                    <v-btn color="primary" @click="$router.push('/datatable')">ดูข้อมูล</v-btn>
                  </template>
                </v-data-table>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-app>
  </template>
  
  <script>
  import axios from "axios";
  
  export default {
    data() {
      return {
        headers: [
          { text: 'ID', value: 'id' },
          { text: 'Name', value: 'name' },
          { text: 'Email', value: 'email' },
          { text: 'Status', value: 'status' },
          { text: 'Actions', value: 'actions', sortable: false }
        ],
        items: []
      };
    },
  
    async created() {
      await this.fetchData();
    },
  
    methods: {
      async fetchData() {
        try {
          const response = await axios.get("http://localhost:7000/data");
          this.items = response.data;
        } catch (error) {
          console.error("Error fetching data:", error);
        }
      },
  
      viewDetails(item) {
        console.log("View details for:", item);
        // Implement view details functionality
      },
  
      editItem(item) {
        console.log("Edit item:", item);
        // Implement edit item functionality
      },
  
      deleteItem(item) {
        console.log("Delete item:", item);
        // Implement delete item functionality
      },
  
      addNewItem() {
        console.log("Add new item");
        // Implement add new item functionality
      }
    }
  };
  </script>
  
  <style scoped>
  .v-toolbar {
    background-color: #0e62b5;
    color: white;
  }
  
  .v-data-table th {
    background-color: #e3f2fd;
  }
  
  .v-btn.primary {
    background-color: #1e88e5 !important;
  }
  
  .v-card-title {
    background-color: #42a5f5;
    color: white;
  }
  </style>
  