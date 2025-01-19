<template>
  <div id="Directions">
    <div class=" grid grid-cols-12 mt-4 shadow-md">
      <div class="col-span-2 mx-auto">
        <div>
          <ArrowIcon :size="35" />
        </div>

        <div class="h-16 mt-4 w-full">
          <div :class="[isPickupActive ? 'circle-black' : 'circle-gray']"></div>
          <div class="line"></div>
          <div :class="[!isPickupActive ? 'square-black' : 'square-gray']"></div>
        </div>
      </div>

      <div class="col-span-10 pr-4">
        <div class="w-full h-5">

        </div>
        
        <div class="mb-2 bt-5">
          <AutoCompleteInput theId="firstInput" v-model="pickup" placeholder="Enter pick-up location" @isActive="isPickupActive = true" />
        </div>

        <div class="mb-3">
          <AutoCompleteInput theId="secondInput" v-model="destination" placeholder="Where to?" @isActive="isPickupActive = false" />
        </div>
      </div>
    </div>

    <div class="flex items-center custom-border-bottom">
      <div class="bg-gray-400 mx-5 my-3.5 p-1.5 rounded-full">
        <MapMarkerIcon :size="30" fillColor="#f5f5f5" />
      </div>
    </div>
  </div>
</template>

<script setup>
  import { ref } from 'vue';
  import AutoCompleteInput from '../components/AutoCompleteInput.vue'
  import ArrowIcon from 'vue-material-design-icons/ArrowLeft.vue'
  import MapMarkerIcon from 'vue-material-design-icons/MapMarker.vue'

  let isPickupActive = ref(true)
  let pickup = ref('')
  let destination = ref('')
</script>

<style lang="scss" scoped>
  #Directions {
    .circle-black, .circle-gray, .square-black, .square-gray, .line {
      margin: 0 auto;
    }

    .circle-black, .circle-gray, .square-black, .square-gray {
      width: 9px;
      height: 9px;
    }

    .bg-custom-color {
      background-color: rgb(237, 237, 237);
    }

    .circle-black, .square-black {
      background-color: black;
    }

    .circle-gray, .circle-black {
      border-radius: 100%;
    }

    .square-gray, .line, .circle-gray {
      background-color: rgb(191, 191, 191);
    }
    
    .line {
      width: 2px;
      height: 45px;
    }

    .custom-border-bottom {
      border-bottom: 1px solid rgb(230, 230, 230);
    }
  }
</style>