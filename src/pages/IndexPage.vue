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
  <EquipmentSettingsFormGenerator :objectGroups="list" />
</template>

<script setup>
import EquipmentSettingsFormGenerator from "../components/EquipmentSettingsFormGenerator.vue";
import dateFormat from "dateformat";
import { ref } from "vue";
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
        name: "testBool",
        title: "Boolean",
        default: true,
        type: "boolean",
      },
      {
        name: "port",
        title: "Порт",
        default: 1,
        min: 1,
        max: 65535,
        type: "number",
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
      // {"name": "auto_reset", "title": "Автосброс", "default": false, "type": "boolean"}
    ],
  },
};
// const list = [
//   { id: 1, type: "text", value: "text Input" },
//   { id: 2, type: "number", value: "688900" },
//   { id: 3, type: "text", value: "text Input 2" },
//   { id: 4, type: "date", value: "2020-12-03" },
//   { id: 5, type: "color", value: "#0000FF" },
// ];
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
