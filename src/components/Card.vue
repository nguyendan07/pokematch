<template>
  <div class="card"
    :class="{ disabled: isDisable }"
    :style="{
      height: `${(750 - 16*4) / Math.sqrt(cardContextLength) - 16}px`,
      width: `${(((750 - 16*4) / Math.sqrt(cardContextLength) - 16) * 3) / 4}px`,
      perspective: `${(((750 - 16*4) / Math.sqrt(cardContextLength) - 16) * 3) / 4 * 2}px`
    }">
    <div
      class="card__inner"
      :class="{ 'is-flipped': isFlipped }"
      @click="onToggleFlipCard"
    >
      <div class="card__face card__face--front">
        <div class="card__content" :style="{
          backgroundSize: `
            ${(((750 - 16*4) / Math.sqrt(cardContextLength) - 16) * 3) / 4 / 3}px
            ${(((750 - 16*4) / Math.sqrt(cardContextLength) - 16) * 3) / 4 / 3}px
          `
        }"></div>
      </div>
      <div class="card__face card__face--back">
        <div class="card__content">
          {{ imgPokemon }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    imgPokemon: {
      type: String,
      required: true,
    },
    card: {
      type: [String, Number, Array, Object],
    },
    cardContextLength: {
      type: Number,
      default: function () {
        return 0
      }
    }
  },
  data() {
    return {
      isFlipped: false,
      isDisable: false,
    };
  },
  methods: {
    onToggleFlipCard () {
      if (this.isDisable) return false;
      this.isFlipped = !this.isFlipped;
      if (this.isFlipped)  this.$emit("onFlip", this.card)
    },
    onFlipBackCard () {
      this.isFlipped = false;
    },
    onEnableDisableMode () {
      this.isDisable = true;
    }
  },
};
</script>

<style lang="css" scoped>
.card {
  display: inline-block;
  margin-right: 1rem;
  margin-bottom: 1rem;
  width: 90px;
  height: 120px;
}

.card.disabled .card__inner {
  cursor: default;
}

.card__inner {
  width: 100%;
  height: 100%;
  transition: transform 1s;
  transform-style: preserve-3d;
  cursor: pointer;
  position: relative;
}

.card__inner.is-flipped {
  transform: rotateY(-180deg);
}

.card__face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  overflow: hidden;
  border-radius: 0.5rem;
  padding: 1rem;
  box-shadow: 0 3px 10px 3px rgba(0, 0, 0, 0.2);
}

.card__face--front .card__content {
  background: url("../assets/images/Poké_Ball_icon.svg") no-repeat center center;
  height: 100%;
  width: 100%;
}

.card__face--back {
  background-color: var(--light);
  transform: rotateY(-180deg);
}

.card__face--back .card__content {
  background-size: contain;
  background-position: center center;
  background-repeat: no-repeat;
  height: 100%;
  width: 100%;
  color: #000;
}
</style>