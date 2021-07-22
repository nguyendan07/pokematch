<template>
  <div class="screen">
    <h1>Interact Component here...</h1>
    <card-flip
      v-for="(card, index) in cardContext"
      :key="index"
      :ref="`card-${index}`"
      :imgPokemon="`images/${card}.png`"
      :card="{ index, value: card }"
      @onFlip="checkRule($event)"
    >
    </card-flip>
  </div>
</template>

<script>
import CardFlip from "./Card.vue";
export default {
  components: {
    CardFlip
  },
  props: {
    cardContext: {
      type: Array,
      default: function () {
        return [];
      }
    }
  },
  data () {
    return {
      rules: []
    }
  },
  methods: {
    checkRule (card) {
      if (this.rules.length === 2) return false;
      this.rules.push(card);
      if (this.rules.length === 2 && this.rules[0].value === this.rules[1].value) {
        console.log("Right....");
        // add class 'disable' to component card
        this.$refs[`card-${this.rules[0].index}`].onEnableDisableMode();
        this.$refs[`card-${this.rules[1].index}`].onEnableDisableMode();

        // reset rules to []
        this.rules = [];

        const disabledElement = document.querySelectorAll(".screen .card.disabled");
        console.log(disabledElement)

        if (disabledElement && disabledElement.length === this.cardContext.length - 2) {
          setTimeout(() => {
            this.$emit("onFinish");
          }, 1000);
        }
      } else if (this.rules.length === 2 && this.rules[0].value !== this.rules[1].value) {
        console.log("Wrong...");
        // close two card
        setTimeout(() => {
          this.$refs[`card-${this.rules[0].index}`].onFlipBackCard();
          this.$refs[`card-${this.rules[1].index}`].onFlipBackCard();
          
          // reset rules to []
          this.rules = [];
        }, 800);
      } else {
        return false;
      }
    }
  }
}
</script>