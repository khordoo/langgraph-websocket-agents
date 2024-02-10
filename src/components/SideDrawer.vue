<template>
<v-navigation-drawer  
        v-model="drawer"
        :rail="rail"
        permanent
        @click="rail = false"
   >
     
        <v-list-item
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
        <v-list density="compact" nav>
          <v-list-item prepend-icon="mdi-home-city" title="Home" value="home"></v-list-item>
          <v-list-item prepend-icon="mdi-account" title="My Account" value="account"></v-list-item>
          <v-list-item prepend-icon="mdi-account-group-outline" title="Users" value="users"></v-list-item>
        </v-list>

        <v-divider></v-divider>


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
    rail: true,

  }),
  methods:{
    toggleSidebar() {
      this.sidebarExpanded = !this.sidebarExpanded;
      this.miniVariant = !this.miniVariant; // Toggle mini-variant state when clicking
    
    },
  }
};
</script>

<style scoped>
.chatHistory{
    text-align: center;
    margin-top: 10px;
}
</style>
