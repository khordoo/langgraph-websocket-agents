<template>
    <div v-if="!messageSent" class="welcome-message">
      <v-row>
        <v-col>
          <h1>Hello, {{ displayName }}</h1>
          <p>How can I help you today?</p>
        </v-col>
      </v-row>
      <!-- Example tiles would go here -->
    </div>
  </template>

<script>
export default {
    name: 'WelcomeMessage',
    props:{
        messageSent: Boolean,
        displayName: String
    }
}
</script>
<style>
.welcome-message{
    margin-top: 50px;
}
</style>