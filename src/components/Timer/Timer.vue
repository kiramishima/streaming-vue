<template>
    <h1 v-if="count > 0">{{ count }}</h1>
    <h1 v-else>Prêt</h1>
</template>


<script lang="ts">
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator';

@Component
export default class TimerComponent extends Vue {
  public count: number = 10;
  private nombres: any = {"1": "Un", "2": "Deux", "3": "Trois", "4": "Quatre", "5": "Cinq", "6": "Six", "7": "Sept", "8": "Huit", "9": "Neuf", "10": "Dix"}
  private ev: any;
  private u!: SpeechSynthesisUtterance;

  created() {
      console.log("Evento Create");
      this.u = new SpeechSynthesisUtterance();
  }

  mounted() {
      console.log("Evento mounted");
      this.ev = setInterval(() => {
        if (this.count > 0) {
            this.u = new SpeechSynthesisUtterance();
            this.u.lang = 'fr-FR';
            this.u.text = this.nombres[this.count.toString()];
            speechSynthesis.speak(this.u);
            this.count--;
        } else {
            this.u = new SpeechSynthesisUtterance();
            this.u.lang = 'fr-FR';
            this.u.text = 'On va commencer';
            clearInterval(this.ev);
        }
      }, 2200)
  }
}
</script>
