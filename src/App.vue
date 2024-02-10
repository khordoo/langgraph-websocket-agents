<template>
  <v-app>
    <!-- Main content area -->
    <v-main app>
      <SideDrawer :displayName="displayName" />

      <v-container fluid class="d-flex justify-center align-center fill-height pa-0" >
        <WelcomeMessage v-if="!messageSent" :messageSent="messageSent" :displayName="displayName" />
        <div v-else class="message-container">
          <v-row>
            <!-- Empty space on the left -->
             <v-col cols="3"></v-col>

            <v-col cols="6" style="background-color: red;">
              <!-- Conditionally show the welcome message or chat history -->
              <div v-if="!messageSent" class="welcome-message">
                <WelcomeMessage :displayName="displayName" />
              </div>
              <div v-else class="message-history">
                <!-- Iterate through messages and show them here -->
                <div v-for="message in messages" :key="message.timestamp.getTime()" class="message"
                  :class="{ 'ai-message': message.sender === 'ai', 'user-message': message.sender === 'user' }">
                  <v-avatar :color="message.sender === 'user' ? 'blue' : 'grey lighten-2'" class="mr-3">
                    <v-icon>{{ message.icon }}</v-icon>
                  </v-avatar>
                  <div class="message-content">
                    <div class="message-header">
                      <!-- Title based on the sender -->
                      <span class="message-title">{{ message.sender === 'user' ? 'You' : 'ChatGPT' }}</span>
                    </div>
                    <div class="message" >{{ message.text }}</div>
                  </div>
                </div>
              </div>
            </v-col>
            <!-- Empty space on the left -->
            <v-col cols="3"></v-col>
          </v-row>
        </div>

      </v-container>
      <div class="input-container">
        <MessageInput @sendMessage="handleSendMessage" style="background-color: red;" />
      </div>


    </v-main>


  </v-app>
</template>


<script>
import MessageInput from './components/MessageInput.vue';
import SideDrawer from './components/SideDrawer.vue';
import WelcomeMessage from './components/WelcomeMessage.vue';

export default {
  name: 'App',
  components: {
    MessageInput,
    SideDrawer,
    WelcomeMessage
  },
  data: () => ({
    sidebarExpanded: true,
    miniVariant: false, // Controls whether the drawer is in its mini state
    messageSent: false,
    userMessage: '',
    messages: [],
    displayName: 'John Dow'
  }),
  methods: {
    handleSendMessage(message) {
      this.userMessage = message;
      this.messages.push({
        sender: "user",
        text: message,
        icon: "mdi-account",
        timestamp: new Date()
      });
      this.messageSent = true;
      // Send the message to the AI agent
      // TODO: Send the message to the AI agent and get the response
      // For the purpose of this example, we'll simulate an AI response
      setTimeout(() => {
        this.messages.push({
          text: "This is an AI response.",
          sender: 'ai',
          icon: 'mdi-creation-outline',
          timestamp: new Date()
        });
      }, 1000); // Simulate a delay for the AI response


    }
  },
};
</script>

<style>
.fill-height {
  min-height: 0;
  /* Reset min-height */
  height: calc(100vh - 48px);
  /* Adjust the 48px based on your v-app-bar height if you have one */
}

.welcome-message {
  margin-top: 50px;
}

.message-input {
  padding: 0;
  margin: 0;
  /* Adjust height as necessary, but only as much as needed */
  height: auto;
  margin-left: 20px;
}

.input-container {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  /* Ensures full width */
  padding: 0 16px;
  /* Optional: Adjust padding if needed */
}

.message-history {
  display: flex;
  flex-direction: column;
  justify-content: flex-start; /* Align messages to the start of the flex container */
  overflow-y: auto;
  flex-grow: 1;
  max-height: calc(100vh - 120px); /* Adjust the 120px to account for your input area and any headers/footers */
  min-height: 0; /* Override Vuetify's default min-height */
  width: 100%;
}

.message {
  display: flex;
  align-items: flex-start;
  /* Align items to the start to handle multi-line text */
  margin-bottom: 12px;
  width: 100%;
}

.message-content {
  max-width: 100%;
  width: 100%;
  /* Prevents the message text from stretching too wide */
}

.message-header {
  display: flex;
  align-items: center;
}

.message-title {
  font-weight: bold;
  margin-right: 8px;
}

.message-text {
  margin-top: 4px;
  width: 100%;
  /* If you want to separate the title from the text */
}</style>
