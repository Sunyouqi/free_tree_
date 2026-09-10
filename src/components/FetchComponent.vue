<script setup lang="ts">
import { ref } from 'vue'

const message = ref('')
const username = ref('')
const postResponse = ref('')

const BACKEND_URL = 'http://10.136.195.144:5000'

//NATIVE FETCH: GET Request
async function fetchMessage() {
  try {
    const response = await fetch(`${BACKEND_URL}/data`)
    if (!response.ok) throw new Error('Network response error')

    const data = await response.json()
    message.value = data.message
  } catch (error) {
    console.error('Error fetching data:', error)
  }
}

async function sendUser() {
  try {
    const response = await fetch(`${BACKEND_URL}/submit`, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json', //Tells Flask to expect JSON
      },
      body: JSON.stringify({
        username: username.value,
      }), //Must stringify the body
    })
    if (!response.ok) throw new Error('Network response error')

    const data = await response.json()
    postResponse.value = data.message
  } catch (error) {
    console.error(' Error sending data:', error)
  }
}
</script>

<template>
  <div class="container">
    <!--Get Session -->
    <h1>Vue + Flask Connection</h1>
    <button @click="fetchMessage">Get Backend Message</button>

    <p v-if="message">{{ message }}</p>
    <hr />
    <!--Post Session -->
    <input v-model="username" placeholder="Enter username" />
    <button @click="sendUser">Send to Backend</button>
    <p v-if="postResponse">{{ postResponse }}}</p>
  </div>
</template>
<script lang="ts">
export default {
  compatConfig: { MODE: 3 },
}
</script>
<style scoped lang="scss"></style>
