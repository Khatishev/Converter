<template>
    <div class="container">
        <h2>Weight Converter</h2>
        <input type="number" v-model="inputWeight">
        <select v-model="selectedWeightFrom">
        <option value="kilograms">Kilograms</option>
        <option value="pounds">Pounds</option>
        <option value="ounces">Ounces</option>
        </select>
        <span>=</span>
        <span>{{ convertedWeight }}</span>
        <select v-model="selectedWeightTo">
        <option value="kilograms">Kilograms</option>
        <option value="pounds">Pounds</option>
        <option value="ounces">Ounces</option>
        </select>
    </div>
</template>

  <script>
  export default {
    data() {
        return {
            inputWeight: 0,
            selectedWeightFrom: 'kilograms',
            selectedWeightTo: 'pounds',
            convertedWeight: 0
        };
    },
    watch: {
        inputWeight: 'convertWeight',
        selectedWeightFrom: 'convertWeight',
        selectedWeightTo: 'convertWeight'
    },
    methods: {
        convertWeight() {
            if (this.selectedWeightFrom === 'kilograms') {
                if (this.selectedWeightTo === 'pounds') {
                    this.convertedWeight = this.inputWeight * 2.20462;
                } else if (this.selectedWeightTo === 'ounces') {
                    this.convertedWeight = this.inputWeight * 35.27396;
                } else {
                    this.convertedWeight = this.inputWeight;
                }
            } else if (this.selectedWeightFrom === 'pounds') {
                if (this.selectedWeightTo === 'kilograms') {
                    this.convertedWeight = this.inputWeight / 2.20462;
                } else if (this.selectedWeightTo === 'ounces') {
                    this.convertedWeight = this.inputWeight * 16;
                } else {
                    this.convertedWeight = this.inputWeight;
                }
            } else if (this.selectedWeightFrom === 'ounces') {
                if (this.selectedWeightTo === 'kilograms') {
                    this.convertedWeight = this.inputWeight / 35.27396;
                } else if (this.selectedWeightTo === 'pounds') {
                    this.convertedWeight = this.inputWeight / 16;
                } else {
                    this.convertedWeight = this.inputWeight;
                }
            }
        }
    }
  };
  </script>

<style scoped></style>