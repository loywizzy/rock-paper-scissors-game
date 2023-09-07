<script>
import { ref } from 'vue'

export default {
  data() {
    return {
      player1ImgUrl: new URL('./img/p1.png', import.meta.url).href,
      player2ImgUrl: new URL('./img/p2.png', import.meta.url).href,
      result: 'Click Play!!',
      player1score: 0,
      player2score: 0
    }
  },

  methods: {
    playGame() {
      const player1 = Math.floor(Math.random() * 4) + 1
      const player2 = Math.floor(Math.random() * 4) + 1

      if (player1 === 1) {
        this.player1ImgUrl = new URL('./img/rock.png', import.meta.url).href
      } else if (player1 === 2) {
        this.player1ImgUrl = new URL('./img/scissors.png', import.meta.url).href
      } else if (player1 === 4) {
        this.player1ImgUrl = new URL('./img/heart.png', import.meta.url).href
      } else {
        this.player1ImgUrl = new URL('./img/paper.png', import.meta.url).href
      }

      if (player2 === 1) {
        this.player2ImgUrl = new URL('./img/rock.png', import.meta.url).href
      } else if (player2 === 2) {
        this.player2ImgUrl = new URL('./img/scissors.png', import.meta.url).href
      } else if (player2 === 4) {
        this.player2ImgUrl = new URL('./img/heart.png', import.meta.url).href
      } else {
        this.player2ImgUrl = new URL('./img/paper.png', import.meta.url).href
      }

      if (player1 === player2) {
        this.result = 'Draw!'
      } else if (
        (player1 === 1 && player2 === 2) ||
        (player1 === 2 && player2 === 3) ||
        (player1 === 3 && player2 === 1) ||
        (player1 === 4 && player2 === 2) ||
        (player1 === 4 && player2 === 3) ||
        (player1 === 4 && player2 === 1)
        
      ) {
        this.result = 'Player 1 Win'
        this.player1score++
      } else {
        this.result = 'Player 2 Win'
        this.player2score++
      }
    },
    
    restartGame() {
      this.player1ImgUrl = new URL('./img/p1.png', import.meta.url).href,
      this.player2ImgUrl = new URL('./img/p2.png', import.meta.url).href,
      this.result = 'Click Play!!',
      this.player1score = 0,
      this.player2score = 0
    }
  }
}

</script>


<template>
  <div>
    <h1>เกมเป่ายิ้งฉุบบบบบ</h1>
    <div >
      <div>
        <h2>Player1</h2>
        <img :src="player1ImgUrl" />
      </div>
        <h2>Player2</h2>
      <div>
        <img :src="player2ImgUrl" />
      </div>
    </div>
    <p>{{ result }}</p>
    <p>Score : {{ player1score }} - {{ player2score }}</p>
    <button @click="playGame">Play!!</button> <button @click="restartGame">Restart!!</button>
  </div>
</template>