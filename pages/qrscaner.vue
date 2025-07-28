<template>
  <v-container class="py-10">
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-card class="rounded-2xl shadow-lg p-4">
          <!-- QR Code Scanner Area -->
          <v-card-title class="text-xl font-bold text-center justify-center">
            QR Code Scanner
          </v-card-title>

          <v-card-text>
            <div
              id="reader"
              class="mx-auto my-4 rounded-md border border-gray-300"
              style="width: 100%; max-width: 400px;"
            ></div>

            <!-- Scanned Result Display -->
            <div v-if="scannedText" class="mt-6">
              <v-alert type="success" border="start" colored-border elevation="2">
                <strong>Scanned Result:</strong><br />
                {{ scannedText }}
              </v-alert>
            </div>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { Html5QrcodeScanner } from 'html5-qrcode'

// Store scanned QR result
const scannedText = ref('')

// QR code successful scan handler
const onScanSuccess = (decodedText) => {
  console.log('✅ QR Code:', decodedText)
  scannedText.value = decodedText
}

// Optional: scan failure logging
const onScanFailure = (error) => {
  console.warn('Scan error:', error)
}

// Mount QR code scanner
onMounted(() => {
  const html5QrcodeScanner = new Html5QrcodeScanner(
    'reader',
    { fps: 10, qrbox: { width: 250, height: 250 } },
    false
  )
  html5QrcodeScanner.render(onScanSuccess, onScanFailure)
})
</script>

<style scoped>
#reader {
  background-color: #5e5e5e;
  padding: 8px;
  border-radius: 8px;
}
</style>
