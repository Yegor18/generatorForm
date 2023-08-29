<template>
  <EquipmentSettingsFormGenerator v-model="modelValue" :objectGroups="list" />
</template>

<script setup>
import EquipmentSettingsFormGenerator from "../components/EquipmentSettingsFormGenerator.vue";
import { ref } from "vue";
const modelValue = ref({
  test_form: {
    my_var: "true",
    my_var2: 2,
    my_var4: 579,
  },
});

const list = {
  test_form: {
    title: "Подключение",
    fields: [
      {
        name: "my_var",
        title: "Адрес",
        default: "127.0.0.1",
        MaxLenght: 150,
        type: "text",
      },
      {
        name: "my_var2",
        title: "Порт",
        default: 1,
        min: 1,
        max: 65535,
        type: "number",
      },
      {
        name: "my_var3",
        title: "Порт",
        default: 1,
        min: 1,
        max: 65535,
        type: "number",
      },
    ],
  },
};
</script>
