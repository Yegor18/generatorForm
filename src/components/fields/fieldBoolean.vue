<template>
  <label :for="fieldProperties.boolParams.name" class="label">{{
    fieldProperties.boolParams.title
  }}</label>
  <q-checkbox
    :name="fieldProperties.boolParams.name"
    v-model="modelValue"
    style="width: 200px"
  />
</template>
<script setup>
import { ref } from "vue";
const fieldProperties = defineProps(["boolParams"]);
let modelValue = ref(fieldProperties.boolParams.default);
</script>
<style lang="sass">
.label
  font-weights:bold
</style>
