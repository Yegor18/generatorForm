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
            <FieldNumber :numberParams="field" />
          </template>
          <template v-if="field.type === 'text'">
            <FieldText :textParams="field" />
          </template>
          <template v-if="field.type === 'boolean'">
            <FieldBoolean :boolParams="field" />
          </template>
          <template v-if="field.type === 'widget_com_port'">
            <FieldWidgetComPortSelect :comPortParams="field" />
          </template>
          <br />
        </template>
      </template>
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
import FieldNumber from "./fields/fieldNumber.vue";
import FieldText from "./fields/fieldText.vue";
import FieldBoolean from "./fields/fieldBoolean.vue";
import FieldWidgetComPortSelect from "./fields/FieldWidgetComPortSelect.vue";
const groupsFields = defineProps({ objectGroups: Object });
let obj = {};
for (let group in groupsFields.objectGroups) {
  let mas = [];
  for (let field in groupsFields.objectGroups[group].fields) {
    let obj2 = {};
    obj2[field.name] = field.default ? obj2[field.default] : null;
    mas.push(obj2);
  }
  obj[group] = mas;
}
console.log("This is object ", obj);

// let elementRefs = ref({});
// for (let el of groupsFields) {
//   if (el.type === "date") {
//     let date = new Date(el.value);
//     el.value = dateFormat(date, "yyyy-mm-dd");
//   }
//   elementRefs.value[el.id] = el.value;
// }
</script>
