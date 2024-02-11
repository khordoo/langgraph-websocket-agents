<template>
    <div v-for="message in messages" :key="message.timestamp.getTime()" class="message">
        <div class="icon-and-title">
            <v-icon class="message-icon"  >{{ message.icon }}</v-icon>
            <span class="message-title">{{ message.sender === 'user' ? 'You' : 'AI' }}</span>
        </div>

        <div class="message-text">{{ message.text }}</div>
    </div>
</template>

<script>
export default {
    props: {
        messages: []
    }
}

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
  margin-top: 40px;
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
  font-size: 1rem;
  font-family: Helvetica, sans-serif;
}
.message-title {
  font-weight: bold;
  margin-left: 5px;
}
.v-icon {
  margin-right: 4px; /* Adjust space between the icon and the title */
  size: 48;

}
.message-icon{
    color: #AB68FF;
}

.icon-and-title {
  display: flex;
  align-items: center;
  margin-bottom: 10px; /* Adjust the space below the title as needed */
  margin-left: 10px;
}

</style>
