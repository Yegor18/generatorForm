<template>
  <label :for="fieldProperties.params.name" class="label">{{
    fieldProperties.params.title
  }}</label>
  <q-input
    type="number"
    :name="fieldProperties.params.name"
    v-model="modelValue"
    :min="fieldProperties.params.min"
    :max="fieldProperties.params.max"
    style="width: 200px"
    @update:model-value="
      (value) => {
        if (value > fieldProperties.params.max) {
          modelValue = fieldProperties.params.max;
        } else if (value < fieldProperties.params.min) {
          modelValue = fieldProperties.params.min;
        }
        emits('change', value);
      }
    "
  />
</template>
<script setup>
import { ref } from "vue";
const fieldProperties = defineProps(["params"]);
const emits = defineEmits(["change"]);
let modelValue = ref(
  fieldProperties.params.modelValue
    ? fieldProperties.params.modelValue
    : fieldProperties.params.default
);
</script>
<style lang="sass" scoped>
.label
  font-weight: bold
</style>
