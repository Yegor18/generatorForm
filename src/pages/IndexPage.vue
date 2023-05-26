<template>
  <template v-for="element in list" :key="element.id">
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
  </template>
</template>

<script setup>
import dateFormat from "dateformat";
import { ref } from "vue";
const list = [
  { id: 1, type: "text", value: "text Input" },
  { id: 2, type: "number", value: "688900" },
  { id: 3, type: "text", value: "text Input 2" },
  { id: 4, type: "date", value: "2020-12-03" },
  { id: 5, type: "color", value: "#0000FF" },
];
let elementRefs = ref([]);
for (let el of list) {
  if (el.type === "date") {
    let date = new Date(el.value);
    el.value = dateFormat(date, "yyyy-mm-dd");
  }
  elementRefs.value[el.id] = el.value;
}
//почему не работает ссылка v-model на поле объекта?
//Например
//<q-input v-model="element.elementRefs"></q-input>
//<script setup>
//for (let element of list) {
// element.elementRefs = ""
//}
//</setup>
</script>

<style lang="sass" scoped>
.my-picker
  max-width: 250px
</style>
