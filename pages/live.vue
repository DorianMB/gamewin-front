<template>
  <div class="live">
    <h1 class="title">
      League of legends <b-badge>Off</b-badge>
    </h1>
    <div class="d-flex w-100">
      <iframe :src="live" frameborder="0"
              allowfullscreen="true" scrolling="no" height="500" width="70%"></iframe>
      <iframe
        id="chat_embed"
        :src="chat"
        scrolling="no" style="border:0"
        height="500"
        width="30%">
      </iframe>
    </div>
  </div>
</template>

<script>
export default {
  name: "bet",
  data: () => {
    return {
      channel: 'riotgames',
      parent: 'localhost',
    }
  },
  computed: {
    live() {
      return 'https://player.twitch.tv/?channel='+this.channel+'&parent='+this.parent;
    },
    chat()  {
      return 'https://www.twitch.tv/embed/'+this.channel+'/chat?parent='+this.parent;
    }
  }
}
</script>

<style scoped lang="scss">
  .live {
    padding: 3rem 5rem;
  }
</style>
