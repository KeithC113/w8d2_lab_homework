<template>
  <div id="app">
    <sightings-form />
    <sightings-grid :sightings="sightings" />
  </div>
</template>

<script>
import SightingsForm from './components/SightingsForm';
import SightingsGrid from './components/SightingsGrid';
import SightingService from './services/SightingService.js';

export default {
  name: 'app',
  components: {
    'sightings-form': SightingsForm,
    'sightings-grid': SightingsGrid
  },
  data() {
    return {
      sightings: []
    };
  },
	mounted() {
    this.fetchSightings();
  },
  methods: {
    fetchSightings() {
      SightingService.getSightings()
        .then(sightings => this.sightings = sightings);
    }
  }
}
</script>

<style>
html {
  height: 100%;
}

body {
  background: url('./assets/birds-background.jpg') no-repeat;
  height: 100%;
  background-position: center;
  background-repeat: repeat;
  background-size: cover;

}
</style>
