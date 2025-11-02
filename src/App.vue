<template>
  <div class="app">
    <CustomizedCode />
    <ColorControlPanel
      :colorVars="colorVars"
      @onChangeColor="onChangeColor"
      @onRestoreColor="onRestoreColor"
      @onRestoreColors="onRestoreColors"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
import { initColorValues } from "./data/initColorValues";
import ColorControlPanel from "./components/ColorControlPanel.vue";
import CustomizedCode from "./components/CustomizedCode.vue";

const backgroundColor = ref(initColorValues.backgroundColor);
const tagsColor = ref(initColorValues.tagsColor);
const symbolsColor = ref(initColorValues.symbolsColor);
const variablesColor = ref(initColorValues.variablesColor);
const commentsColor = ref(initColorValues.commentsColor);
const functionsColor = ref(initColorValues.functionsColor);
const directivesColor = ref(initColorValues.directivesColor);
const keywordsColor = ref(initColorValues.keywordsColor);
const stringsColor = ref(initColorValues.stringsColor);
const propertiesTypesColor = ref(initColorValues.propertiesTypesColor);
const valuesColor = ref(initColorValues.valuesColor);

const colorVars = {
  backgroundColor,
  tagsColor,
  symbolsColor,
  variablesColor,
  commentsColor,
  functionsColor,
  directivesColor,
  keywordsColor,
  stringsColor,
  propertiesTypesColor,
  valuesColor,
};

const onChangeColor = (params) => {
  colorVars[params.contentToChange].value = params.event.target.value;
};

const onRestoreColor = (colorToRestore) => {
  colorVars[colorToRestore].value = initColorValues[colorToRestore];
};

const onRestoreColors = () => {
  Object.keys(colorVars).forEach((colorKey) => {
    colorVars[colorKey].value = initColorValues[colorKey];
  });
};
</script>

<style>
.app {
  height: 100vh;
  background-color: v-bind(backgroundColor);
}

.keys {
  color: #f9d824;
}

.tags {
  color: v-bind(tagsColor);
}

.symbols {
  color: v-bind(symbolsColor);
}

.variables {
  color: v-bind(variablesColor);
}

.comments {
  color: v-bind(commentsColor);
}

.functions {
  color: v-bind(functionsColor);
}

.directives {
  color: v-bind(directivesColor);
}

.keywords {
  color: v-bind(keywordsColor);
}

.strings {
  color: v-bind(stringsColor);
}

.properties-types {
  color: v-bind(propertiesTypesColor);
}

.values {
  color: v-bind(valuesColor);
}
</style>
