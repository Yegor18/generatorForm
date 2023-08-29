<template>
  <label :for="fieldProperties.params.name" class="label">{{
    fieldProperties.params.title
  }}</label>
  <div style="max-width: 200px">
    <q-select
      v-model="modelValue"
      :options="options"
      label="Standard"
      @update:modelValue="
        (newValue) => {
          modelValue = newValue;
          emits('change', newValue);
        }
      "
    />
  </div>
</template>
<script setup>
import { ref } from "vue";
const fieldProperties = defineProps(["params"]);
let options = ref(fieldProperties.params.options);
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
