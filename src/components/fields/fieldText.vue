<template>
  <label :for="fieldProperties.textParams.name" class="label">{{
    fieldProperties.textParams.title
  }}</label>
  <q-input
    type="text"
    :name="fieldProperties.textParams.name"
    :modelValue="modelValue"
    @update:modelValue="
      (newValue) => {
        modelValue = newValue;
        emit('change', newValue);
      }
    "
    style="width: 200px"
    :maxlength="fieldProperties.textParams.MaxLenght"
  />
</template>
<script setup>
import { ref } from "vue";
const fieldProperties = defineProps(["textParams"]);
const emit = defineEmits(["change"]);
let modelValue = ref(fieldProperties.textParams.default);
</script>
<style lang="sass">
.label
  font-weights:bold
</style>
