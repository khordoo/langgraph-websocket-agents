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
              <MessageHistory :messages="messages" ></MessageHistory>
            </template>
          </v-col>
          <v-col cols="3"></v-col> <!-- Right spacer -->
        </v-row>
      </v-container>
      <v-row>
        <v-col cols="3"></v-col> <!-- Left spacer -->
        <v-col cols="6"  style="background-color: red;" ></v-col> <!-- Left spacer -->
        <v-col cols="3"></v-col> <!-- Left spacer -->
      </v-row>
      <div class="input-container">
        <MessageInput @sendMessage="handleSendMessage" />
      </div>
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
.v-container{
   background-color: #353541;
}
.message-area {
  height: calc(100vh - 60px);
  /* Height minus input area height */
  overflow-y: auto;
  /* Enable scrolling for overflow content */
}

.input-container {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
}

.message {
  margin: 8px 0;
  /* Spacing between messages */
}

.icon-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.message-text {
  padding-left: 15px;
  margin-top: 4px;
  margin-bottom: 30px;
}
.message-title {
  font-weight: bold;
  margin-left: 5px;
  margin-top: 5px;
}
.v-icon {
  margin-right: 4px; /* Adjust space between the icon and the title */
  size: 48;
}

.icon-and-title {
  display: flex;
  align-items: center;
  margin-bottom: 10px; /* Adjust the space below the title as needed */
  margin-left: 10px;
}

</style>
