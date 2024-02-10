<template>
  <v-app>
   
    <SideDrawer :displayName="displayName" />
    <v-main>
      <v-container class="d-flex justify-center align-cente">
        
        <div v-if="!messageSent" class="welcome-message">
          <WelcomeMessage :messageSent="messageSent" :displayName="displayName"  />
        </div>

        <div v-else class="message-container">
          <v-row>
            <v-col>
              <v-chip class="user-message" color="blue" text-color="white">
                <v-avatar left>
                  <v-img src="user_icon.png"></v-img>
                </v-avatar>
                {{ userMessage }}
              </v-chip>
              <!-- AI response would go here -->
            </v-col>
          </v-row>
        </div>
      </v-container>
    </v-main>

    <MessageInput @sendMessage="handleSendMessage" />
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
    displayName:'John Dow'
  }),
  methods: {
    handleSendMessage(message) {
      this.userMessage = message;
      this.messageSent = true;
      // Send the message to the AI agent
    }
  },
};
</script>

<style>
.welcome-message{
  margin-top: 50px;
}
</style>
