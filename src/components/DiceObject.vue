<template>
  <div class="dices-container">
    <div :class="[piece, color, 'square']"></div>
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
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.square {
  width: 200px;
  height: 200px;
}
</style>
