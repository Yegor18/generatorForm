<template>
  <!-- <template v-for="element in list" :key="element.id">

    <template v-if="element.type === 'text'">
      <q-input
        v-model="elementRefs[element.id]"
        type="text"
        style="width: 200px; height: 200px"
        >{{ element.value }}</q-input
      >
    </template>
    <template v-if="element.type === 'number'">
      <q-input
        v-model="elementRefs[element.id]"
        type="number"
        style="width: 200px; height: 200px"
        >{{ element.value }}</q-input
      >
    </template>
    <template v-if="element.type === 'date'">
      <q-input
        v-model="elementRefs[element.id]"
        type="date"
        style="width: 200px; height: 200px"
        >{{ element.value }}</q-input
      >
    </template>
    <template v-if="element.type === 'color'">
      <q-color :model-value="elementRefs[element.id]" class="my-picker" />
      Hello people
    </template>
  </template> -->
  <EquipmentSettingsFormGenerator v-model="modelValue" :objectGroups="list" />
</template>

<script setup>
import EquipmentSettingsFormGenerator from "../components/EquipmentSettingsFormGenerator.vue";
import dateFormat from "dateformat";
import { ref } from "vue";
const modelValue = {
  device_settings_connection: [
    {
      path: "value",
    },
    {
      port: "value",
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
};
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
      // {
      //   name: "testBool",
      //   title: "Boolean",
      //   default: true,
      //   type: "boolean",
      // },
      {
        name: "port",
        title: "Порт",
        default: 1,
        min: 1,
        max: 65535,
        type: "number",
      },
      // {
      //   name: "port",
      //   title: "Порт",
      //   default: "Facebook",
      //   options: ["Google", "Facebook", "Twitter", "Apple", "Oracle"],
      //   type: "widget_com_port",
      // },
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
// let elementRefs = ref({});
// for (let el of list) {
//   if (el.type === "date") {
//     let date = new Date(el.value);
//     el.value = dateFormat(date, "yyyy-mm-dd");
//   }
//   elementRefs.value[el.id] = el.value;
// }
</script>

<style lang="sass" scoped>
.my-picker
  max-width: 250px
</style>
