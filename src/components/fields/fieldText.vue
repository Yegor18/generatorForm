<template>
  <label :for="fieldProperties.textParams.name" class="label">{{
    fieldProperties.textParams.title
  }}</label>
  <q-input
    type="text"
    :name="fieldProperties.textParams.name"
    v-model="modelValue"
    style="width: 200px"
    :maxlength="fieldProperties.textParams.MaxLenght"
  />
</template>
<script setup>
import { ref } from "vue";
const fieldProperties = defineProps(["textParams"]);
let modelValue = ref(fieldProperties.textParams.default);
</script>
<style lang="sass">
.label
  font-weights:bold
</style>
