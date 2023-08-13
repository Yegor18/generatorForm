<template>
  <label :for="fieldProperties.numberParams.name" class="label">{{
    fieldProperties.numberParams.title
  }}</label>
  <q-input
    type="number"
    :name="fieldProperties.numberParams.name"
    v-model="modelValue"
    :min="fieldProperties.numberParams.min"
    :max="fieldProperties.numberParams.max"
    style="width: 200px"
    @update:model-value="
      (value) => {
        if (value > fieldProperties.numberParams.max) {
          console.log('We have reached maximum limit ', value);
          modelValue = fieldProperties.numberParams.max;
        } else if (value < fieldProperties.numberParams.min) {
          console.log('We have reached minimum limit ', value);
          modelValue = fieldProperties.numberParams.min;
        }
      }
    "
  />
</template>
<script setup>
import { ref } from "vue";
const fieldProperties = defineProps(["numberParams"]);
let modelValue = ref(fieldProperties.numberParams.default);
</script>
<style lang="sass">
.label
  font-weights:bold
</style>
