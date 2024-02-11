<template>
      <div v-if="showSuggestions" class="suggestion-holder">
        <v-row>
      <!-- Loop through your suggestions and create two cards per row -->
      <v-col
        v-for="(suggestion, index) in suggestions"
        :key="index"
        cols="12"
        sm="6" 
        md="6" 
        class="pb-4"
      >
        <v-card flat 
        class="suggestion-card mx-auto" 
        border-color="red"
        variant="outlined"
        prepend-icon="mdi-lightbulb-outline" 
         @click="handleSuggestionClick(suggestion.text)" >
            <template v-slot:title>
                {{ suggestion.title }}
            </template>
            <v-card-title class="text-h6"> </v-card-title>
          <!-- <v-card-subtitle>{{ suggestion.subtitle }}</v-card-subtitle> -->
          <v-card-text>This is text{{ suggestion.subtitle }}</v-card-text>
        </v-card>
      </v-col>
    </v-row>
      </div>
      <v-text-field
        label="Message Assistant..."
        v-model="message"
        @keyup.enter="send"
        append-inner-icon="mdi-microphone"
        prepend-inner-icon="mdi-paperclip"
        variant="outlined"
        clearable
        single-line
        hide-details
      ></v-text-field>

  </template>
  
  <script>
  export default {
    name: 'MessageInput',
    props:{
        showSuggestions: Boolean
    },
    data: () => ({
      message: '',
      suggestions: [
      { title: 'Actions', text: 'and answer questions' },
      { title: 'Human in the loop', text: 'and explain about it' },
      { title: 'Notification', text: 'and how it is done' },
      { title: 'Monitoring', text: 'and how it is done' },
    
      // Add more suggestions as needed
    ],
    }),
    methods: {
      send() {
        this.$emit('sendMessage', this.message);
        this.message = ''; // Clear the input after sending
      },
      handleSuggestionClick(suggestion) {
      // Emit an event or call method to handle suggestion click
      this.message=suggestion
      console.log(suggestion.title); // Replace with your logic
    }
    },
  };
  </script>
  
  <style> 

.v-text-field {
border-radius: 10px; /* This should match the border-radius of the input field inside MessageInput */
  overflow: hidden; /* To ensure the border-radius applies to all inner elements */
  background-color: transparent; /* No background to blend with the page */
  box-shadow: none; /* Remove box shadow if it's not needed */
  width: 100%;
  margin-bottom: 50px;
  padding: 12px;
  font-size: 1rem;
  border-radius: 20px;
}
.v-card{
    padding-top: .75rem;
    padding-bottom: 0.75rem;
    padding: 12px;
    background-color: #353541;
    border-radius: 20px;
}
.suggestion-card{
    border-color: white;
    background-color: #353541;
}
.suggestion-holder{
    margin-bottom: 30px;
    background-color: transparent;
}
.v-col{
    background-color: transparent;
}

  </style>
  
 