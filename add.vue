<template>
    <div>
      <!-- Main Heading -->
      <h1 :title="id">{{ msg }}</h1>
      
      <!-- Status Display -->
      <div>
        <h1>{{ status }}</h1>
      </div>
      
      <!-- Button with Icon -->
      <div>
        <v-btn class="ma-2" color="primary">
          {{ status }}
          <v-icon icon="mdi-checkbox-marked-circle" end></v-icon>
        </v-btn>
      </div>
      
      <!-- Progress Circular Components -->
      <div>
        <h1>Temp</h1>
        <v-progress-circular :model-value="value" :rotate="360" :size="100" :width="15" color="teal">
          <template v-slot:default>{{ value }} %</template>
        </v-progress-circular>
        
        <h1>Humi</h1>
        <v-progress-circular :model-value="value1" :rotate="360" :size="100" :width="15" color="red">
          <template v-slot:default>{{ value1 }} %</template>
        </v-progress-circular>
      </div>
      
      <!-- Input and Button -->
      <div>
        <input v-model="id" type="text" />
        <button @click="add">CLICK</button>
      </div>
    </div>
  </template>
  
  <script>
  import mqtt from "mqtt";
  
  export default {
    data() {
      return {
        id: 10,
        name: "hello",
        msg: "",
        sw: "",
        status: "",
        value: 12,
        value1: 60,
        retryTimes: 0
      };
    },
  
    created() {
      this.client = mqtt.connect("ws://broker.emqx.io:8083/mqtt");
      this.client.on("connect", this.onMqttConnect);
      this.client.on("message", this.onMqttMessage);
      this.client.on("reconnect", this.handleOnReConnect);
    },
  
    beforeDestroy() {
      if (this.client) {
        this.client.end();
      }
    },
  
    methods: {
      add() {
        const sw = this.id++;
        this.value = sw;
        this.client.publish("room1/sw01", String(sw));
      },
  
      onMqttConnect() {
        console.log("connected");
        this.status = "Mqtt connected";
        this.client.publish("op", "status");
        this.client.subscribe("status", (err) => err && console.error(err));
        this.client.subscribe("room1/sw01", (err) => err && console.error(err));
      },
  
      onMqttMessage(topic, message) {
        if (topic === "status") {
          console.log("GOT:", message.toString());
          this.msg = message.toString();
        }
        if (topic === "room1/sw01") {
          console.log("lamp 1 On");
          this.value = message.toString();
        }
      },
  
      handleOnReConnect() {
        this.retryTimes += 1;
        if (this.retryTimes > 5) {
          try {
            this.client.end();
            this.initData();
            this.$message.error("Connection maxReconnectTimes limit, stop retry");
          } catch (error) {
            this.$message.error(error.toString());
            console.log("Connection failed", error);
            this.status = "Mqtt Disconnected";
          }
        }
      },
    },
  };
  </script>
  
  <style scoped>
  /* Add scoped styles here if needed */
  </style>
  