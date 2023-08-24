<template>
  <label :for="fieldProperties.dateParams.name" class="label">{{
    fieldProperties.dateParams.title
  }}</label>
  <q-input
    :modelValue="modelValue"
    :name="fieldProperties.dateParams.name"
    :value="modelValue"
    type="date"
    @update:modelValue="
      (newValue) => {
        modelValue = newValue;
        emits('change', newValue);
      }
    "
    >{{ modelValue }}</q-input
  >
</template>
<script setup>
import { ref } from "vue";
const fieldProperties = defineProps(["dateParams"]);
const emits = defineEmits(["change"]);
// console.log("data params ", fieldProperties.dateParams);
// let date = new Date(fieldProperties.dateParams.default);
let modelValue = ref(fieldProperties.dateParams.default);
// console.log("dddaaate ", fieldProperties.dateParams.default, date);
//let modelValue = ref(dateFormat(date, "yyyy-mm-dd"));
</script>
<style lang="sass">
.label
  font-weights:bold
</style>
