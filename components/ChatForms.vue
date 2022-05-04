<template>
  <v-flex xs-12>
    <v-text-field
      label="Писать тут, потом читать там"
      single-line
      v-model="text"
      @keydown.enter="send"
    />
  </v-flex>
</template>

<script>
export default {
  data: () => ({
    text: '',
  }),
  methods: {
    send() {
      this.$socket.emit('createMessage', {
        rext: this.text,
        id: this.$store.state.user.id
      }, data => {
        if (typeof data === 'string') {
          console.error(data);
        } else {
          this.text = '';
        }
      })
    }
  }
}
</script>