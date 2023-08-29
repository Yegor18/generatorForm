<template>
  <label :for="fieldProperties.params.name" class="label">{{
    fieldProperties.params.title
  }}</label>
  <q-checkbox
    :name="fieldProperties.params.name"
    v-model="modelValue"
    @update:model-value="
      (value) => {
        emits('change', value);
      }
    "
    style="width: 200px"
  />
</template>
<script setup>
import { ref } from "vue";
const fieldProperties = defineProps(["params"]);
let modelValue = ref(
  fieldProperties.params.modelValue
    ? fieldProperties.params.modelValue
    : fieldProperties.params.default
);
const emits = defineEmits(["change"]);
</script>
<style lang="sass" scoped>
.label
  font-weight: bold
</style>
