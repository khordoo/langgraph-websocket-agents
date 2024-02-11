<template>
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
    data: () => ({
      message: '',
    }),
    methods: {
      send() {
        this.$emit('sendMessage', this.message);
        this.message = ''; // Clear the input after sending
      },
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
  padding: 2px;
}

  </style>
  
  