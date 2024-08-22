<template>
  <TemperatureConverter />
  <WeightConverter />
</template>

<script>
import TemperatureConverter from './components/TemperatureConverter.vue';
import WeightConverter from './components/WeightConverter.vue';

export default {
  components: {
    TemperatureConverter,
    WeightConverter
  }
};
</script>

<style></style>