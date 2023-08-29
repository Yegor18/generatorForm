<template>
  <template v-for="(group, groupKey) in props.objectGroups" :key="groupKey">
    <div v-if="group.title">{{ group.title }}</div>

    <template v-for="(field, fieldKey) in group.fields" :key="fieldKey">
      <component
        v-if="field.type in fields"
        :is="fields[field.type]"
        :params="{
          modelValue: props.modelValue[groupKey]
            ? props.modelValue[groupKey][field.name]
              ? props.modelValue[groupKey][field.name]
              : field.default
            : field.default,
          ...field,
        }"
        @change="(value) => updateModelValue(groupKey, field.name, value)"
      ></component>
      <div v-else>Компонент поля {{ field.type }} не найден</div>

      <br />
    </template>
  </template>
</template>
<script setup>
import FieldNumber from "./fields/fieldNumber.vue";
import FieldText from "./fields/fieldText.vue";
import FieldBoolean from "./fields/fieldBoolean.vue";
import FieldWidgetComPortSelect from "./fields/fieldWidgetComPortSelect.vue";

const props = defineProps(["objectGroups", "modelValue"]);
const emit = defineEmits(["update:modelValue"]);

const fields = {
  number: FieldNumber,
  text: FieldText,
  boolean: FieldBoolean,
  widget_com_port: FieldWidgetComPortSelect,
};

createModelValue();

function createModelValue() {
  let newModelValue = structuredClone(props.modelValue);
  for (let group in props.objectGroups) {
    if (!newModelValue[group]) newModelValue[group] = {};
    let propsValue = {};
    for (let field of props.objectGroups[group].fields) {
      propsValue[field.name] = field.default;
    }

    newModelValue[group] = Object.assign(propsValue, newModelValue[group]);
  }
  emit("update:modelValue", newModelValue);
}

function updateModelValue(group, field, value) {
  let newModelValue = structuredClone(props.modelValue);
  if (Object.keys(newModelValue[group]).includes(field)) {
    newModelValue[group][field] = value;
  }

  emit("update:modelValue", newModelValue);
}
</script>
