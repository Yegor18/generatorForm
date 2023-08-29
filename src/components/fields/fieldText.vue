<template>
  <label :for="fieldProperties.params.name" class="label">{{
    fieldProperties.params.title
  }}</label>
  <q-input
    type="text"
    :name="fieldProperties.params.name"
    :modelValue="modelValue"
    @update:modelValue="
      (newValue) => {
        modelValue = newValue;
        emits('change', newValue);
      }
    "
    style="width: 200px"
    :maxlength="fieldProperties.params.MaxLength"
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
