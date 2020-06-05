<template>
    <div id="preparing">
      Wait until everybody joined the game...
      <button @click="startGame">Start</button>
    </div>
</template>

<script>
import {store} from '../../store'

export default {
    name: 'Preparing',
    methods: {
        startGame: () => {
            store.dispatch('startGame')
        }
    }
}
</script>

<style scoped>

</style>