<template>
  <v-layout justify-end align-end>
    <v-flex md6>
      <v-card>
        <v-toolbar color="primary" dark>
          <v-toolbar-title>
            Chat
          </v-toolbar-title>
        </v-toolbar>
        <lista v-if="mensajes.length > 0" :mensajes="mensajes" />
        <v-card-text>
          <v-text-field @keyup.enter="enviarSMS" ref="txtMensaje" v-model="texto" solo hide-details/>
        </v-card-text>
        <v-card-text v-if="mostrarEmojis">
          <emoji @recibeEmoji="addEmoji" :caracter="item.caracter" v-for="(item, index) in emojis" :key="index" />
          <!-- :style="'grid-row: ' + item.fila + '; grid-column: ' + item.columna + ';'" -->
        </v-card-text>
        <v-btn icon flat @click="mostrarEmojis = !mostrarEmojis">
          <v-icon v-if="!mostrarEmojis">insert_emoticon</v-icon>
          <v-icon v-else>close</v-icon>
        </v-btn>
        </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import Emoji from './Emoji.vue'
import Lista from './Lista.vue'

export default {
  components: { Emoji, Lista },
  data() {
    return {
      emojis: [
        { caracter: '😃', fila: 1, columna: 1 },
        { caracter: '😄', fila: 1, columna: 2 },
        { caracter: '😅', fila: 1, columna: 3 },
        { caracter: '😆', fila: 1, columna: 4 },
        { caracter: '😉', fila: 1, columna: 5 },
        { caracter: '😊', fila: 2, columna: 1 },
        { caracter: '😋', fila: 2, columna: 2 },
        { caracter: '😢', fila: 2, columna: 3 },
        { caracter: '😍', fila: 2, columna: 4 },
        { caracter: '😳', fila: 2, columna: 5 },
        { caracter: '😱', fila: 3, columna: 1 },
        { caracter: '😤', fila: 3, columna: 2 },
        { caracter: '😲', fila: 3, columna: 3 },
        { caracter: '🙁', fila: 3, columna: 4 },
        { caracter: '😔', fila: 3, columna: 5 },
        { caracter: '🎉', fila: 4, columna: 1 },
        { caracter: '🎁', fila: 4, columna: 2 },
        { caracter: '🎈', fila: 4, columna: 3 },
        { caracter: '❤️', fila: 4, columna: 4 },
        { caracter: '👍', fila: 4, columna: 5 }        
      ],
      texto: '',
      mensajes: [],
      mostrarEmojis: false
    }
  },
  methods: {
    addEmoji(emoji) {
      this.texto += emoji
      this.$refs.txtMensaje.focus()
    },
    enviarSMS() {
      if (this.texto.length > 0) {
        this.mensajes.push(this.texto)
        this.texto = ''
      }
    }
  }
}
</script>