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
        emits('change', newValue);
      }
    "
    style="width: 200px"
    :maxlength="fieldProperties.textParams.MaxLenght"
  />
</template>
<script setup>
import { ref } from "vue";
const fieldProperties = defineProps(["textParams"]);
const emits = defineEmits(["change"]);
let modelValue = ref(fieldProperties.textParams.default);
</script>
<style lang="sass">
.label
  font-weights:bold
</style>
