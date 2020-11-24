<template>
  <div class="container">
    <div class="w-100">
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
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
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
})
</script>

<style lang="scss">
  .container {
    margin: 0 auto;
    min-height: 98vh;
    display: flex;
    justify-content: center;
    text-align: center;
    padding-top: 3rem;
  }

  .button--green, .button--grey {
    background: white;
  }

  .links {
    padding-top: 15px;
  }
</style>
