<template>
  <div class="dices-container">
    <div :class="squareColor">
      <div :class="[piece, color, 'square', { animate: doAnimation }]"></div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-property-decorator";

@Component
export default class DicesObject extends Vue {
  @Prop({ type: String })
  piece!: "pawn" | "knight" | "bishop" | "rook" | "queen" | "king";

  @Prop({ type: String })
  color!: "white" | "black";

  @Prop({ type: String, default: "" })
  squareColor?: "";

  doAnimation = false;

  animate(): void {
    this.doAnimation = true;
    setTimeout(() => {
      this.doAnimation = false;
    }, 200);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.square {
  width: 200px;
  height: 200px;
  transition: transform 0.2s ease-in-out;

  &.animate {
    transform: scale(1.05);
  }
}

.black-square {
  background: rgba(0, 0, 0, 0.7);
}

.white-square {
  background: rgba(255, 255, 255, 0.7);
}
</style>
