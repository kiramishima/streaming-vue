<template>
    
    <v-container>
        <v-layout row wrap>
            <v-flex xs12>
                <v-img src="https://picsum.photos/510/300?random" aspect-ratio="1.7"></v-img>
            </v-flex>
        </v-layout>
    </v-container>


</template>

<script lang="ts">
import Vue from 'vue'
import { Component, Prop } from 'vue-property-decorator';

@Component
export default class CardComponent extends Vue {
  @Prop() private msg!: string;
  private u!: SpeechSynthesisUtterance;

  created() {
      console.log("Evento Create");
      // this.u = new SpeechSynthesisUtterance();
  }

  mounted() {
      console.log("Evento mounted");
      /*setTimeout(() => {
        this.u.lang = 'fr-FR';
        this.u.text = 'Bienvenu a ce stream';
        speechSynthesis.speak(this.u);
      }, 1500)*/
  }
}
</script>
