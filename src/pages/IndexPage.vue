<template>
  <EquipmentSettingsFormGenerator v-model="modelValue" :objectGroups="list" />
</template>

<script setup>
import EquipmentSettingsFormGenerator from "../components/EquipmentSettingsFormGenerator.vue";
import { ref } from "vue";
const modelValue = ref({
  device_settings_connection: [
    {
      path: "value",
    },
    {
      port: "value",
    },
    {
      option: "value",
    },
  ],
  device_settings_connection_parameters: [
    {
      coil_value: "value",
    },
    {
      delay_value: "value",
    },
    {
      auto_reset_value: "value",
    },
    { auto_reset: "value" },
  ],
});
const list = {
  device_settings_connection: {
    title: "Подключение",
    fields: [
      {
        name: "path",
        title: "Адрес",
        default: "127.0.0.1",
        MaxLenght: 150,
        type: "text",
      },
      {
        name: "port",
        title: "Порт",
        default: 1,
        min: 1,
        max: 65535,
        type: "number",
      },
      {
        name: "option",
        title: "Соц сеть",
        default: "Facebook",
        options: ["Google", "Facebook", "Twitter", "Apple", "Oracle"],
        type: "widget_com_port",
      },
    ],
  },
  device_settings_connection_parameters: {
    title: "Параметры подключения",
    fields: [
      {
        name: "coil_value",
        title: "Вход (Coil)",
        default: 0,
        min: 0,
        max: 2040,
        type: "number",
      },
      {
        name: "delay_value",
        title: "Задержка (мс)",
        default: 0,
        min: 0,
        max: 10000,
        type: "number",
      },
      {
        name: "auto_reset_value",
        title: "Автосброс через (мс)",
        default: 0,
        min: 0,
        max: 10000,
        type: "number",
      },
      {
        name: "auto_reset",
        title: "Автосброс",
        default: false,
        type: "boolean",
      },
    ],
  },
};
</script>

<style lang="sass" scoped>
.my-picker
  max-width: 250px
</style>
