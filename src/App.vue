<template>
  <v-app>
    <v-toolbar app color="primary" dark>
      <v-toolbar-title class="headline">
        <span>{{titulo}}</span>
      </v-toolbar-title>
    </v-toolbar>

    <v-content>
      <v-container fill-height fluid>
        <chat />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import Chat from '@/components/practicaS03/Chat.vue'

export default {
  components: {Chat},
  name: 'App',
  data() {
    return {
      titulo: 'Chat with Vue + Vuetify'
    }
  }
}
</script>
