<template>
  <div>
    <v-btn icon class="emoji" @click="enviaEmoji">{{ caracter }}</v-btn>
  </div>
</template>

<script>
export default {
  props: ['caracter'],
  methods: {
    enviaEmoji() {
      this.$emit('recibeEmoji', this.caracter)
    }
  }
}
</script>

<style>
.emoji {
  font-size: 24px;
}
</style>
