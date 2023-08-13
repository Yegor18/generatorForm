<template>
  <div class="q-pa-md" style="max-width: 300px">
    <div class="q-gutter-md">
      <q-select v-model="model" :options="options" label="Standard" />
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
const fieldProperties = defineProps(["comPortParams"]);
let model = ref(fieldProperties.comPortParams.default);
let options = ref(fieldProperties.comPortParams.options);
</script>
