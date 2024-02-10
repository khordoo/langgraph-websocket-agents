<template>
    <v-card fixed="true" class="ma-5 pa-3" tile>
      <v-text-field
        label="Enter a prompt here"
        v-model="message"
        @keyup.enter="send"
        outlined
        clearable
        single-line
      ></v-text-field>
    </v-card>
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
  /* Style your component */
  </style>
  