<script setup>
import {computed, ref} from "vue";

const hexMessage = ref("12342012902016192024e020260e20287a202c30203210203fbd2041f9204abc20600f2062e4206804206997207ee620832120863e209f3e20a8e720abb920b14020b85620cbed20e2ff20e9b7")
const hexWords = ref([])
const words = computed(()=>{
  return hexMessage.value.toUpperCase().split("20")
})
const hexOutput = computed(()=>{
  return hexWords.value.join("20")
})
const appendGlyph = (word)=>{
  hexWords.value = [...hexWords.value,word]
}
</script>


<template>
  <main>
    <textarea v-model="hexMessage" cols="160"></textarea>
    <p >{{hexOutput}}</p>
    <div style="display: flex;flex-wrap: wrap;">
      <figure v-for="word in words"  @click="appendGlyph(word)">

      <img  :src="'symbols/'+word+'.png'" style="width: 50%"
     />
        <figcaption>{{word}}</figcaption>
      </figure>
    </div>
  </main>
</template>

<style scoped>

</style>
