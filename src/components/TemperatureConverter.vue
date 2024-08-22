<template>
  <div class="container">
    <h2>Temperature Converter</h2>
    <input type="number" v-model="inputTemp">
    <select v-model="selectedFrom">
      <option value="celsius">Celsius</option>
      <option value="fahrenheit">Fahrenheit</option>
      <option value="kelvin">Kelvin</option>
    </select>
    <span>=</span>
    <span>{{ convertedTemp }}</span>
    <select v-model="selectedTo">
      <option value="celsius">Celsius</option>
      <option value="fahrenheit">Fahrenheit</option>
      <option value="kelvin">Kelvin</option>
    </select>
  </div>
</template>

<script>
export default {
    data() {
        return {
            inputTemp: 0,
            selectedFrom: 'celsius',
            selectedTo: 'fahrenheit',
            convertedTemp: 0
        };
    },
    watch: {
        inputTemp: 'convertTemperature',
        selectedFrom: 'convertTemperature',
        selectedTo: 'convertTemperature'
    },
    methods: {
        convertTemperature() {
            if (this.selectedFrom === 'celsius') {
                if (this.selectedTo === 'fahrenheit') {
                    this.convertedTemp = (this.inputTemp * 9/5) + 32;
                } else if (this.selectedTo === 'kelvin') {
                    this.convertedTemp = parseFloat(this.inputTemp) + 273.15;
                } else {
                    this.convertedTemp = this.inputTemp;
                }
            } else if (this.selectedFrom === 'fahrenheit') {
                if (this.selectedTo === 'celsius') {
                    this.convertedTemp = (this.inputTemp - 32) * 5/9;
                } else if (this.selectedTo === 'kelvin') {
                    this.convertedTemp = (this.inputTemp - 32) * 5/9 + 273.15;
                } else {
                    this.convertedTemp = this.inputTemp;
                }
            } else if (this.selectedFrom === 'kelvin') {
                if (this.selectedTo === 'celsius') {
                    this.convertedTemp = parseFloat(this.inputTemp) - 273.15;
                } else if (this.selectedTo === 'fahrenheit') {
                    this.convertedTemp = (parseFloat(this.inputTemp) - 273.15) * 9/5 + 32;
                } else {
                    this.convertedTemp = this.inputTemp;
                }
            }
        },
    }
};
</script>

<style scoped></style>