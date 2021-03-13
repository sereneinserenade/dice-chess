<template>
  <div class="dices-container">
    <div class="dices">
      <dice-object :color="entity[1]" :piece="entity[0]" />
    </div>

    <div class="buttons">
      <div class="button black-button" @click="roll()">
        Roll
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import DiceObject from "./DiceObject.vue";

@Component({
  components: {
    DiceObject
  }
})
export default class Dices extends Vue {
  entity: Array<string> = [];

  indices: Array<number> = [1, 2, 3, 4, 5, 6];

  squareColor = "";

  entities: Record<number, string> = {
    1: "pawn",
    2: "knight",
    3: "bishop",
    4: "rook",
    5: "queen",
    6: "king"
  };

  roll(): void {
    const index = Math.floor(Math.random() * 6);
    const entityKey = this.indices[index];
    const piece = this.entities[entityKey];
    this.squareColor = "";
    this.entity = [];
    this.entity.push(piece);
    if (piece === "bishop") {
      const index = Math.floor(Math.random() * 3);
      if (index === 1) {
        this.entity.push("white");
        return;
      }
      if (index === 2) {
        this.entity.push("black");
        return;
      }
    }
    this.entity.push("white");
  }

  mounted(): void {
    this.roll();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.dices {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

.buttons {
  display: flex;
  flex-direction: row;
  justify-content: center;

  .button {
    height: 100px;
    width: 100px;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 1rem;
    cursor: pointer;
    font-size: 1.2rem;
    font-weight: bold;

    &.white-button {
      background: white;
      color: rgba(0, 0, 0, 0.8);
    }

    &.black-button {
      background: black;
      color: rgba(255, 255, 255, 0.8);
    }
  }
}
</style>
