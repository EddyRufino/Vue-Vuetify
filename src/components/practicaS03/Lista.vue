<template>
  <v-layout column>
    <v-layout justify-end v-for="(item, index) in mensajes" :key="index">
      <v-card color="secondary" dark class="ma-2 pa-2 mensaje">
        <span>{{ item }}</span>
      </v-card>
    </v-layout>
  </v-layout>
</template>

<script>
export default {
  props: ['mensajes']
}
</script>

<style>
.mensaje {
  border-radius: 10px;
}
</style>
