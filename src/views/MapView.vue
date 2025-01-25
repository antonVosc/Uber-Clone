<template>
  <div id="MapView">
    <div id="map"></div>
  </div>
</template>

<script setup>
  import { onMounted } from 'vue';

  onMounted(() => {
    setTimeout(() => {
      initMap()
    }, 50)
  })

  const initMap = () => {
    const map = new window.google.maps.Map(document.getElementById("map"), {
      center: { lat: -34.397, lng: 150.644 },
      zoom: 8,
      fullScreenControl: false,
      zoomControl: false,
      streetViewControl: false,
      mapTypeControl: false,
    });
  }
</script>

<style lang="scss">
  #MapView {
    #map {
      width: 100%;
      height: 45vh;
      top: 0px;
      left: 0px;
    }

    .gm-style-cc {
      display: none;
    }

    .bg-custom-color {
      background-color: rgb(237, 237, 237);
    }
  }
</style>