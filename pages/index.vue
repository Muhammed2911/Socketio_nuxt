<template>
  <div id="home">
    <button type="button" class="btn btn-primary" @click="getMessage">
      Click Me
    </button>
    {{ messageRxd }}
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      socket: null,
      messageRxd: null,
    }
  },
  mounted() {
    this.socket = this.$nuxtSocket({
      name: 'home',
      channel: '/index',
    })
  },
  methods: {
    async getMessage() {
      this.messageRxd = await this.socket.emitP('getMessage')
    },
  },
}
</script>
