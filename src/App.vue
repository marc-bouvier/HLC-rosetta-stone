<script setup>
import {computed, ref} from "vue";

const englishMapping = {
  "1234": "together",
  "1290": "you",
  "3210": "us",
  "1619": "take it from me",
  "24E0": "arrived not?",
  "260E": "build?",
  "287A": "speak",
  "2C30": "???",
  "3FBD": "arrived?",
  "41F9": "closed? / lucky?",
  "4ABC": "présenter",
  "600F": "cohabiter, refuge",
  "62E4": "E2FF,260E -> arriver, build? -> coloniser?/envahir?",
  "6804": "open?",
  "6997": "observer / regarder / défendre",
  "7EE6": "2C30,260E",
  "8321": "présenter not",
  "863E": "not",
  "9F3E": "nouveau / naissance / début",
  "A8E7": "maison",
  "ABB9": "love?",
  "B140": "give ?",
  "B856": "partir",
  "CBED": "paix",
  "E2FF": "arriver",
  "E9B7": "explorer / témoin de / découvrir",
}

const hexMessage = ref("12342012902016192024e020260e20287a202c30203210203fbd2041f9204abc20600f2062e4206804206997207ee620832120863e209f3e20a8e720abb920b14020b85620cbed20e2ff20e9b7")
const hexWords = ref([])
const englishWords = ref([])
const words = computed(() => {
  return hexMessage.value.toUpperCase().split("20")
})
const hexOutput = computed(() => {
  return hexWords.value.join("20")
})
const englishOutput = computed(() => {
  return englishWords.value.join(" ")
})
const appendGlyph = (word) => {
  hexWords.value = [...hexWords.value, word]
  englishWords.value = [...englishWords.value, englishMapping[word.toUpperCase()]]
}
</script>


<template>
  <main>
    <textarea v-model="hexMessage" cols="160"></textarea>
    <p>{{ hexOutput }}</p>
    <p>{{ englishOutput }}</p>
    <div style="display: flex;flex-wrap: wrap;">
      <figure v-for="word in words" @click="appendGlyph(word)" style="pointer">

        <img :src="`symbols/${word}.png`" style="width: 20%"
        />
        <figcaption>{{ word }} - {{englishMapping[word]}}</figcaption>
      </figure>
    </div>
  </main>
</template>

<style scoped>

</style>
