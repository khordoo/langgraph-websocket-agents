<template>
  <v-app>
    <v-main>
      <SideDrawer :displayName="displayName" />
      <v-container fluid>
        <v-row>
          <v-col cols="3"></v-col> <!-- Left spacer -->
          <v-col cols="6" class="message-area">
            <template v-if="!messages.length">
              <!-- Welcome message -->
              <WelcomeMessage :displayName="displayName" />
            </template>
            <template v-else>
              <MessageHistory :messages="messages"></MessageHistory>
            </template>
          </v-col>
          <v-col cols="3"></v-col> <!-- Right spacer -->
        </v-row>
      </v-container>
      <v-container fluid class="input-container pa-0">
        <v-row justify="center" class="input-container">
          <v-col cols="3"></v-col> <!-- Match the left spacer -->
          <v-col cols="6">
            <MessageInput @sendMessage="handleSendMessage" />
          </v-col>
          <v-col cols="3"></v-col> <!-- Match the right spacer -->
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import MessageInput from './components/MessageInput.vue';
import SideDrawer from './components/SideDrawer.vue';
import WelcomeMessage from './components/WelcomeMessage.vue';
import MessageHistory from './components/MessageHistory.vue';

export default {
  name: 'App',
  components: {
    MessageInput,
    SideDrawer,
    WelcomeMessage,
    MessageHistory
  },
  data: () => ({
    messages: [],
    displayName: 'John Dow'
  }),
  methods: {
    handleSendMessage(message) {
      // Assuming 'mdi-account' is the icon for the user and 'mdi-robot' is the icon for the AI
      this.messages.push({
        sender: "user",
        text: message,
        icon: "mdi-account",
        timestamp: new Date()
      });
      this.messageSent = true;

      // Here you would send the message to the AI and get the response
      // For now, let's simulate an AI response
      setTimeout(() => {
        this.messages.push({
          text: "This is an AI response.",
          sender: 'ChatGPT',
          icon: 'mdi-robot',
          timestamp: new Date()
        });
      }, 1000);
    }
  },
};
</script>

<style>

.v-container {
  background-color: #353541;
}
.input-container{
  background-color: #353541;
 
}

</style>
