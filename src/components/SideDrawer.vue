<template>
<v-navigation-drawer 
        v-model="drawer"
        :rail="rail"
        permanent
        @click="rail = false"
   >
       <div class="content justify-center">


        <v-list-item
          class="useraInfo"
          prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
          :title="displayName"
          nav
        >
         
          <template v-slot:append>
            <v-btn
              variant="text"
              icon="mdi-chevron-left"
              @click.stop="rail = !rail"
            ></v-btn>
          </template>
        </v-list-item>
        <div>
        </div>
        <v-list density="compact" nav>

          <v-list-item @click="newChat" color="primary"   title="New Chat" value="NewChat"  >
            <template v-slot:prepend>
            <v-icon class="new-chat" icon="mdi-plus"></v-icon>
           </template>


          </v-list-item>
        </v-list>

        <v-divider></v-divider>
  
    </div>

    </v-navigation-drawer>


</template>
<script>
export default {
  name: 'SideDrawer',
  props:{
    displayName: String
  },
  components: {
  },
  data: () => ({
    drawer: true,
    rail: false,

  }),
  methods:{
    newChat() {
    this.$emit('new-chat');
  },
  }
};
</script>

<style scoped>


</style>
