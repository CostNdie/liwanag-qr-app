<template>
  <div class="d-flex align-center justify-center" style="height: 100vh;">

    <v-card width="500" class="pa-8">
    <h1 class="text-center my-6">Login Page</h1>
      <div class="text-subtitle-1 text-medium-emphasis justify-center"></div>

      <v-text-field
        density="compact"
        placeholder="Username"
        prepend-inner-icon="mdi-email-outline"
        outlined
        rounded
        
      ></v-text-field>

      <div class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between">
        

        <a
          class="text-caption text-decoration-none text-blue"
          href="#"
          rel="noopener noreferrer"
          target="_blank"
        >
          </a>
      </div>

      <v-text-field
        :append-inner-icon="visible ? 'mdi-eye-off' : 'mdi-eye'"
        :type="visible ? 'text' : 'password'"
        density="compact"
        placeholder="Password"
        prepend-inner-icon="mdi-lock-outline"
        outlined
        rounded
        @click:append-inner="visible = !visible"
      ></v-text-field>

      <v-card
        class="mb-8"
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
        rounded="xl"
      >
        Log In
      </v-btn>
      <div class="text-center my-6">OR</div>
      <v-btn color="error" @click="signinWithGoogle()" rounded="xl" class="text-capitalize" block><v-icon left>mdi-google</v-icon> Sign in With google</v-btn>
      <v-card-text class="text-center">
        <a
          class="text-blue text-decoration-none"
          href="#"
          rel="noopener noreferrer"
          target="_blank"
        >
          <v-icon icon="mdi-chevron-right"></v-icon>
        </a>
      </v-card-text>
    </v-card>
  </div>
</template>
<script setup>
  import { ref } from 'vue'

  const visible = ref(false)
</script>
<script>
export default {
    layout: "auth",
    middleware: "guest",
    methods:{
      signinWithGoogle(){
        this.$auth.loginWith('google')
      }
    }
}
</script>
