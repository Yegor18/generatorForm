<template>
  <template
    v-for="(group, groupKey) in groupsFields.objectGroups"
    :key="groupKey"
  >
    <template v-for="(element, elementKey) in group" :key="elementKey">
      <div
        v-if="elementKey === 'title'"
        :for="element"
        style="font-weight: bold"
      >
        {{ element }}<br />
      </div>
      <template v-if="elementKey === 'fields'">
        <template v-for="field in element" :key="field.name">
          <template v-if="field.type === 'number'">
            <fieldNumber :numberParams="field" />
          </template>
          <template v-if="field.type === 'text'">
            <fieldText :textParams="field" />
          </template>
          <template v-if="field.type === 'boolean'">
            <fieldBoolean :boolParams="field" />
          </template>
          <br />
        </template>
      </template>
      <!-- <template v-if="element.type === 'number'">
        <q-input
          v-model="elementRefs[element.id]"
          type="number"
          style="width: 200px; height: 200px"
          >{{ element.value }}</q-input
        >
        HELLO WORLD
      </template> -->
      <!-- <template v-if="element.type === 'date'">
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
      </template> -->
    </template>
  </template>
</template>
<script setup>
import { ref } from "vue";
import fieldNumber from "./fields/fieldNumber.vue";
import fieldText from "./fields/fieldText.vue";
import fieldBoolean from "./fields/fieldBoolean.vue";
const groupsFields = defineProps({ objectGroups: Object });
// let elementRefs = ref({});
// for (let el of groupsFields) {
//   if (el.type === "date") {
//     let date = new Date(el.value);
//     el.value = dateFormat(date, "yyyy-mm-dd");
//   }
//   elementRefs.value[el.id] = el.value;
// }
</script>
