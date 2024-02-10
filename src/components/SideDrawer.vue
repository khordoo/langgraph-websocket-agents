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
          <v-list-item prepend-icon="mdi-cog" title="Settings" value="settings"></v-list-item>
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

  })
};
</script>

<style scoped>
.chatHistory{
    text-align: center;
    margin-top: 10px;
}
</style>
