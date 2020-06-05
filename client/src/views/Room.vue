<template>
  <div class="room">
    <Chat id="chat" />
    <Game id="game" />
    <ShotLog id="shot-log" />
  </div>
</template>

<script>
// @ is an alias to /src
import Chat from '@/components/Chat.vue'
import Game from '@/components/Game.vue'
import ShotLog from '@/components/Busfahrer/ShotLog.vue'

export default {
  name: 'Room',
  components: {
    Chat,
    Game,
    ShotLog
  }
}
</script>

<style scoped>
#chat{
  margin: auto;
  height:0px;
  overflow: scroll;
}
#game{
  margin: auto
}

#shot-log{
  background-color: aqua;
  height: 10px;
  overflow: scroll;
}
</style>