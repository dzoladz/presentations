<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  mainEntry: {
    //
    type: String,
    default: "Main Entry"
  },
  partOfSpeech: {
    // noun
    type: String,
    default: "",
  },
  pronunciation: {
    // prə-ˌnən(t)-sē-ˈā-shən
    type: String,
    default: ""
  },
  syllables: {
    // syl·la·ble
    type: String,
    default: ""
  },
  definitions: {
    type: Array,
    default: []
  }
})

</script>

<template>
  <div class="h-full">
    <div>
      <span class="text-6xl font-bold" style="font-family: 'Playfair Display'">{{ mainEntry }}</span>
      <span v-if="partOfSpeech" class="text-4xl pl-5" style="font-family: 'Playfair Display'">{{ partOfSpeech }}</span>
    </div>
    <div class="mt-2 text-2xl">
      <span v-if="syllables" class="">{{ syllables }}</span>
      <span v-if="pronunciation" class="pl-5">{{ pronunciation }}</span>
    </div>
    <div class="mt-2">
      <div v-for="(definition, index) in definitions" >
        <div class="flex">
          <div class="w-1/24">
            <div class="font-bold text-xl">{{ index + 1 }}</div>
          </div>
          <div class="w-23/24 text-xl">{{ definition }}</div>
        </div>
      </div>
    </div>
  </div>
</template>
