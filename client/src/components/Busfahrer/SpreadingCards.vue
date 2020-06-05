<template>
    <div>
      Spreading Cards
      

      <div id="others-cards">
        <div id="player-one" class="card-box">
          <div class="three-cards">
            <div v-for="card in cards" :key="card" class="playingCards fourColours rotateHand">

              <div v-if="card !== 'x'">
                <Card v-bind:value="card.value" v-bind:color="card.color" />
              </div>
              <div v-else>
              </div>

            </div>

          </div>
          {{ player1 }}
        </div>

        <div id="player-two" class="card-box">
          <div class="three-cards">
            <div v-for="card in cards" :key="card" class="playingCards fourColours rotateHand">

              <div v-if="card !== 'x'">
                <Card v-bind:value="card.value" v-bind:color="card.color" />
              </div>
              <div v-else>
              </div>

            </div>

          </div>
          {{ player2 }}
        </div>

        <div id="player-three" class="card-box">
          <div class="three-cards">
            <div v-for="card in cards" :key="card" class="playingCards fourColours rotateHand">

              <div v-if="card !== 'x'">
                <Card v-bind:value="card.value" v-bind:color="card.color" />
              </div>
              <div v-else>
              </div>

            </div>
          </div>
          {{ player3 }}
        </div>

        <div id="player-four" class="card-box">
          <div class="three-cards">
            <div v-for="card in cards" :key="card" class="playingCards fourColours rotateHand">

              <div v-if="card !== 'x'">
                <Card v-bind:value="card.value" v-bind:color="card.color" />
              </div>
              <div v-else>
              </div>

            </div>

          </div>
          {{ player4 }}
        </div>

        <div id="player-five" class="card-box">
          <div class="three-cards">
            <div v-for="card in cards" :key="card" class="playingCards fourColours rotateHand">

              <div v-if="card !== 'x'">
                <Card v-bind:value="card.value" v-bind:color="card.color" />
              </div>
              <div v-else>
              </div>

            </div>

          </div>
          {{ player5 }}
        </div>

        <div id="player-six" class="card-box">
          <div class="three-cards">
            <div v-for="card in cards" :key="card" class="playingCards fourColours rotateHand">

              <div v-if="card !== 'x'">
                <Card v-bind:value="card.value" v-bind:color="card.color" />
              </div>
              <div v-else>
              </div>

            </div>

          </div>
          {{ player6 }}
        </div>

        <div id="player-seven" class="card-box">
          <div class="three-cards">
            <div v-for="card in cards" :key="card" class="playingCards fourColours rotateHand">

              <div v-if="card !== 'x'">
                <Card v-bind:value="card.value" v-bind:color="card.color" />
              </div>
              <div v-else>
              </div>

            </div>

          </div>
          {{ player7 }}
        </div>

      </div>
      
      <div id="your-cards">
        your cards:
        <div class="three-cards">
          <div v-for="card in cards" :key="card" class="playingCards fourColours rotateHand">

            <div v-if="card !== 'x'">
              <Card v-bind:value="card.value" v-bind:color="card.color" />
            </div>
            <div v-else>
            </div>

          </div>

        </div>
      </div>



      <div id="card-ui">


        <template v-if="gameMode === 'colorPick'">
          ColorPick
          <div v-if="players[playerTurn].name === name">
            <button @click="spreadingCardsResp('color', name, 'black')">Black</button>
            <button @click="spreadingCardsResp('color', name, 'red')">Red</button>
          </div>
          <div v-else>
            Not your turn
          </div>
        </template>


        <template v-else-if="gameMode === 'valuePick'">
          valuePick
          <div v-if="players[playerTurn].name === name">
            <button @click="spreadingCardsResp('value', name, 'higher')">Higher</button>
            <button @click="spreadingCardsResp('value', name, 'lower')">Lower</button>
            <button @click="spreadingCardsResp('value', name, 'x')">X</button>
          </div>
          <div v-else>
            Not your turn
          </div>
        </template>


        <template v-else-if="gameMode === 'positionPick'">
          positionPick
          <div v-if="players[playerTurn].name === name">
          <button @click="spreadingCardsResp('position', name, 'inside')">Inside</button>
          <button @click="spreadingCardsResp('position', name, 'outside')">Outside</button>
          <button @click="spreadingCardsResp('position', name, 'x')">x</button>
          </div>
          <div v-else>
            Not your turn
          </div>
        </template>


        <template v-else-if="gameMode === 'spreadingOver'">
          <button @click="nextModeResp()">Flip Cards</button>
        </template>

      </div>

    </div>
</template>

<script>
import {store} from '../../store'
import Card from './Card.vue'

export default {
    name: 'SpreadingCards',
    components: {
      Card
    },
    data: () => {
      return{
        player1: 'tim',
        player2: 'tom',
        player3: 'tan',
        player4: 'jan',
        player5: 'jens',
        player6: 'felix',
        player7: 'joachim'
      }
    },
    computed: {
        players(){
            return store.state.game.players
        },
        name(){
            return store.state.name
        },
        playerTurn(){
            return store.state.game.playerTurn
        },
        gameMode(){
            return store.state.game.gameMode
        },
        playerCards(){
            return store.state.game.playerCards
        },
        cards(){
            let index = this.players.findIndex(obj => obj.name === this.name)
            return this.playerCards[index]
        }
    },
    methods: {
        spreadingCardsResp: (phase, name, pick) => {
            store.dispatch('spreadingCardsResp', {phase: phase, name: name, pick: pick})
        },
        nextModeResp: () => {
            store.dispatch('nextModeResp')
        }
    }
}
</script>

<style scoped>
.three-cards{
  width: 180px;
  height: 80px;
}
.card-box{
  height: 150px;
  width: 180px;
}
#your-cards{
  height: 120px;
  width: 210px;
  position: absolute;
  top: 550px;
  left: 395px;
}
#your-cards .three-cards{
  position: absolute;
  top: 40px
}
#card-ui{
  position: absolute;
  top: 700px;
  height: 120px;
  width: 1000px;
}


#player-one{
  position: absolute;
  top: 525px;
  left: 140px;
}
#player-two{
  position: absolute;
  top: 305px;
  left: 10px;
}
#player-three{
  position: absolute;
  top: 80px;
  left: 140px;
}
#player-four{
  position: absolute;
  top: 20px;
  left: 410px;
}
#player-five{
  position: absolute;
  top: 80px;
  right: 140px;
}
#player-six{
  position: absolute;
  top: 305px;
  right: 10px;
}
#player-seven{
  position: absolute;
  top: 525px;
  right: 140px;
}


#player-one{
  transform: rotate(30deg);
}
#player-two{
  transform: rotate(90deg);
}
#player-three{
  transform: rotate(150deg);
}
#player-four{
  transform: rotate(180deg);
}
#player-five{
  transform: rotate(210deg);
}
#player-six{
  transform: rotate(270deg);
}
#player-seven{
  transform: rotate(330deg);
}
</style>