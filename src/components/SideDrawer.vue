<template>
<v-navigation-drawer v-model="sidebarExpanded" app>
      <v-app-bar-nav-icon  
      expand-on-hoverrail rail
      ></v-app-bar-nav-icon>

      <v-list>
          <v-list-item
            prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
            title="John Dow"
            subtitle="john.down@company.com"
          ></v-list-item>
        </v-list>
        <v-divider></v-divider>
        <div class="d-flex justify-center align-center chatHistory">
            <h5>History</h5>
        </div>
        
<v-list density="compact" nav>
  <v-list-item prepend-icon="mdi-folder" title="How to setup Artifactory" value="How to setup Artifactory"></v-list-item>
  <v-list-item prepend-icon="mdi-account-multiple" title="CDA forms" value="shared"></v-list-item>
  <v-list-item prepend-icon="mdi-star" title="D&A PoC checklist" value="starred"></v-list-item>
</v-list>


    </v-navigation-drawer>


</template>
<script>
export default {
  name: 'SideDrawer',
  components: {
  },
  data: () => ({
    sidebarExpanded: true,
  }),
};
</script>

<style scoped>
.chatHistory{
    text-align: center;
    margin-top: 10px;
}
</style>
