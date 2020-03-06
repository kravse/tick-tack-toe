<template>
  <div>
    <div class="board">
      <cell
        v-for="(key, i) in board"
        :current="key"
        v-bind:key="i"
        @click.native="submitMove(i)">
        </cell>
    </div>
    <div class="win" v-if="winningTeam || isTie">
      <p v-if="isTie">Thats a Tie. Too bad.</p>
      <p v-else>{{this.winningTeam}} Wins!!</p>
      <button @click="reset()">Play Again</button>
    </div>
    <p v-else>Turn: {{turn}}</p>
  </div>
</template>

<script>
import cell from './cell.vue'

export default {
  name: 'board',
  components: {
    cell
  },
  data () {
    return {
      turn: "X",
      board: ["", "", "", "", "", "", "", "", ""],
      lastMove: null
    }
  },
  methods: {
    submitMove: function (square) {
      this.started = true
      if (this.board[square] !== "" || this.winningTeam) return;
      this.$set(this.board, square, this.turn)
      this.turn = this.turn === "X" ? "O" : "X"
    },
    reset: function () {
      this.board = ["", "", "", "", "", "", "", "", ""]
      this.turn = "X"
    }
  },
  computed: {
    isTie: function () {
      return !this.board.includes("") && !this.winningTeam
    },
    winningTeam: function () {
      if (!this.board.includes("X") && !this.board.includes("O")) return false
      let wins = [
        [0, 1, 2],
        [3, 4, 5],
        [6, 7, 8],
        [0, 3, 6],
        [1, 4, 7],
        [2, 5, 8],
        [0, 4, 8],
        [2, 4, 6]
      ]
      // In a production project, I'd find a way to do this without a for loop
      for (let i in wins) {
        if (this.board[wins[i][0]] !== "" &&
          this.board[wins[i][0]] === this.board[wins[i][1]] &&
          this.board[wins[i][1]] === this.board[wins[i][2]]) {
            return this.board[wins[i][0]];
          }
      }
      return ""
    }
  }
};
</script>
<style scoped>
.board {
  display: grid;
  grid-template-columns: 60px 60px 60px;
  grid-template-rows: 60px 60px 60px;
}
.win {
  width: 100%;

}
</style>
