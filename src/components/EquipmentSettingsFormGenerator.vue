<template>
  <template v-for="(group, groupKey) in props.objectGroups" :key="groupKey">
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
            <FieldNumber
              :numberParams="field"
              @change="(value) => updateModelValue(groupKey, field.name, value)"
            />
          </template>
          <template v-if="field.type === 'text'">
            <FieldText
              :textParams="field"
              @change="(value) => updateModelValue(groupKey, field.name, value)"
            />
          </template>
          <template v-if="field.type === 'boolean'">
            <FieldBoolean
              :boolParams="field"
              @change="(value) => updateModelValue(groupKey, field.name, value)"
            />
          </template>
          <template v-if="field.type === 'widget_com_port'">
            <FieldWidgetComPortSelect
              :comPortParams="field"
              @change="(value) => updateModelValue(groupKey, field.name, value)"
            />
          </template>
          <br />
        </template>
      </template>
    </template>
  </template>
</template>
<script setup>
import { ref } from "vue";
import FieldNumber from "./fields/fieldNumber.vue";
import FieldText from "./fields/fieldText.vue";
import FieldBoolean from "./fields/fieldBoolean.vue";
import FieldWidgetComPortSelect from "./fields/FieldWidgetComPortSelect.vue";
const props = defineProps(["objectGroups", "modelValue"]);
const emit = defineEmits(["update:modelValue"]);
console.log("model value ", Object.keys(props.modelValue));
let obj = {};
for (let group in props.objectGroups) {
  let mas = [];
  for (let field of props.objectGroups[group].fields) {
    let obj2 = {};
    obj2[field.name] = field.default ? field.default : null;
    mas.push(obj2);
  }
  obj[group] = mas;
}

function updateModelValue(group, field, value) {
  let obj = structuredClone(props.modelValue);
  console.log("Object  ", obj[group]);
  obj[group].forEach((element, index) => {
    if (Object.keys(element).includes(field)) obj[group][index][field] = value;
  });
  emit("update:modelValue", obj);
  setTimeout(() => console.log("Model value changed ", props.modelValue), 500);
}
</script>
