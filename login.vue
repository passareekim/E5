<template>
    <div>
      <v-img
        class="mx-auto my-6"
        max-width="98"
        src="C:\xampp\htdocs\api_e5\app_e5\img/1.png"
      ></v-img>
  
      <v-card
        class="mx-auto pa-12 pb-8"
        elevation="8"
        max-width="440"
        rounded="lg"
      >
        <div class="text-subtitle-1 text-medium-emphasis">อีเมล</div>
  
        <v-text-field
          v-model = email
          density="compact"
          placeholder="อีเมล"
          prepend-inner-icon="mdi-email-outline"
          variant="outlined"
        ></v-text-field>
  
        <div class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between">
          รหัส
  
          <a
            class="text-caption text-decoration-none text-blue"
            href="#"
            rel="noopener noreferrer"
            target="_blank"
          >
            ลืมรหัสผ่าน</a>
        </div>
  
        <v-text-field
           v-model = passwd
          :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
          :type="visible ? 'text' : 'password'"
          density="compact"
          placeholder="ใส่รหัสผ่าน"
          prepend-inner-icon="mdi-lock-outline"
          variant="outlined"
          @click:append-inner="visible = !visible"
        ></v-text-field>
  
        <v-card
          class="mb-12"
          color="surface-variant"
          variant="tonal"
        >

        </v-card>
  
        <v-btn
          class="mb-8"
          color="blue"
          size="large"
          variant="tonal"
          block
          @click = "doLogin"
        >
          เข้าสู่ระบบ
        </v-btn>
  

      </v-card>
    </div>
  </template>
  <script>
  definePageMeta({
  layout: "custom",
});
  import axios from "axios"
  export default {
    data: () => ({
      visible: false,
      email:'',
      passwd: ''
    }),
    methods:{    
        async doLogin(){
            let forms={
            email: this.email,   
            passwd: this.passwd 
            }
            console.log(forms)
            const response = await axios.post('http://localhost:7000/login',forms)
            const data = response.data
            console.log(data.status)
            if(data.status == "success"){
                console.log(data.row.email)
                window.sessionStorage.setItem("token", JSON.stringify(data.token)); // แบบนี้หาย เมื่อ restart หรือ ปิด  browser                
                this.$router.replace("/datatable");
            }else{
                this.$router.replace("/login");
            }
            }
        }
    }
  
</script>