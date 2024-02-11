<template>
    <div v-if="!messageSent" class="welcome-message">
      <v-row>
        <v-col>
          <h1>Hello, {{ displayName }}</h1>
          <h2>How can I help you today?</h2>
        </v-col>
      </v-row>

    </div>
  </template>

<script>
export default {
    name: 'WelcomeMessage',
    props:{
        messageSent: Boolean,
        displayName: String
    },
}
</script>
<style>
.welcome-message{
    margin-top: 50px;
}
h1{
    font-size: 3.5rem;
    font-family: Google Sans,Helvetica
}


/* Responsive adjustments */
@media (max-width: 600px) {
  .suggestion-card {
    margin: 5px;
  }

  h1 {
    font-size: 2.5rem; /* Smaller size for smaller screens */
  }

  h2 {
    font-size: 1.5rem;
  }
}
</style>