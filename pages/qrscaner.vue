<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <div id="reader" style="width: 100%; max-width: 500px; margin: auto;"></div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { onMounted } from 'vue'
import { Html5QrcodeScanner } from 'html5-qrcode'

const onScanSuccess = (decodedText, decodedResult) => {
  console.log('✅ QR Code:', decodedText)
  
}

const onScanFailure = error => {
  console.warn('Scan error:', error)
}

onMounted(() => {
  const html5QrcodeScanner = new Html5QrcodeScanner(
    'reader',
    { fps: 10, qrbox: { width: 250, height: 250 } },
    false
  )
  html5QrcodeScanner.render(onScanSuccess, onScanFailure)
})
</script>