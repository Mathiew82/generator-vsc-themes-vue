<template>
  <div class="app">
    <CustomizedCode />
    <ColorControlPanel
      :colorVars="colorVars"
      @onChangeColor="onChangeColor"
      @onRestoreColor="onRestoreColor"
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
</script>

<style>
.app {
  height: 100vh;
  background-color: v-bind(backgroundColor);
}

.control-panel {
  width: 250px;
  background-color: white;
  border-radius: 8px;
  color: black;
  padding: 1em;
  position: fixed;
  top: 10px;
  right: 10px;
}

.control-panel h2 {
  margin: 0 0 1em 0;
}

.control-panel input {
  margin-right: 1em;
}

.restore-button {
  background-color: #773333;
  border: none;
  border-radius: 3px;
  color: white;
  cursor: pointer;
  font-size: 11px;
  margin-top: 2px;
  padding: 4px;
}
.restore-button:hover {
  background-color: #995555;
}
.restore-button.all {
  width: 100%;
  font-size: 12px;
  margin-top: 2em;
  padding: 0.6em 0.8em;
}
.restore-button svg {
  width: 16px;
  height: 16px;
}

.generate-code-button {
  width: 100%;
  background-color: #224455;
  border: none;
  border-radius: 8px;
  color: white;
  cursor: pointer;
  margin-top: 1em;
  padding: 0.8em 1em;
}
.generate-code-button:hover {
  background-color: #446677;
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
