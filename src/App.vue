<template>
  <div class="app">
    <pre>
<span class="symbols">&lt;</span><span class="tags">template</span><span class="symbols">&gt;</span>
  <span class="symbols">&lt;</span><span class="tags">input</span>
    <span class="keywords">v-model</span><span class="symbols">="</span><span class="variables">model</span><span class="symbols">"</span>
    <span class="keywords">class</span><span class="symbols">="</span><span class="strings">ui-input py-2 px-5 rounded-full text-sm text-white outline-0</span><span class="symbols">"</span>
    <span class="symbols">:</span><span class="keywords">class</span><span class="symbols">="</span><span class="variables">defaultStyles</span><span class="symbols">"</span>
  <span class="symbols">/&gt;</span>
<span class="symbols">&lt;/</span><span class="tags">template</span><span class="symbols">&gt;</span>

<span class="symbols">&lt;</span><span class="tags">script</span> <span class="keywords">setup lang</span><span class="symbols">="</span><span class="strings">ts</span><span class="symbols">"</span><span class="symbols">&gt;</span>
<span class="directives">import</span> <span class="keys">{</span> <span class="tags">ref</span> <span class="keys">}</span> <span class="directives">from</span> <span class="symbols">'</span><span class="strings">vue</span><span class="symbols">'</span>
<span class="directives">import</span> <span class="keys">{</span> <span class="tags">useType</span> <span class="keys">}</span> <span class="directives">from</span> <span class="symbols">'</span><span class="strings">~/components/ui/composable/useType</span><span class="symbols">'</span>
<span class="directives">import type</span> <span class="keys">{</span> <span class="tags">Event</span> <span class="keys">}</span> <span class="directives">from</span> <span class="symbols">'</span><span class="strings">@/types/Event</span><span class="symbols">'</span>

<span class="keywords">const</span> <span class="variables">model</span> = <span class="functions">defineModel</span><span class="keys">&lt;</span><span class="properties-types">string</span><span class="keys">&gt;</span><span class="keys">()</span>

<span class="keywords">const</span> <span class="keys">{</span> <span class="variables">defaultStyles</span> <span class="keys">}</span> = <span class="functions">useType</span><span class="keys">(</span><span class="symbols">'</span><span class="strings">default</span><span class="symbols">'</span><span class="keys">)</span>

<span class="directives">export</span> <span class="keywords">const</span> <span class="functions">useMyEvents</span> = <span class="keys">()</span> <span class="keywords">=></span> <span class="keys">{</span>
  <span class="keywords">const</span> <span class="functions">addEvent</span> <span class="keywords">=</span> <span class="keys">(</span><span class="values">newEvent</span><span class="keywords">:</span> <span class="tags">Event</span><span class="keys">)</span>: <span class="properties-types">void</span> <span class="keywords">=></span> <span class="keys">{</span>
    <span class="variables">myEvents</span><span class="symbols">.</span><span class="variables">value</span><span class="symbols">.</span><span class="functions">push</span><span class="keys">(</span><span class="values">newEvent</span><span class="keys">)</span>
  <span class="keys">}</span>

  <span class="keywords">const</span> <span class="functions">removeEvent</span> <span class="keywords">=</span> <span class="keys">(</span><span class="values">eventId</span><span class="keywords">:</span> <span class="properties-types">number</span><span class="keys">)</span>: <span class="properties-types">void</span> <span class="keywords">=></span> <span class="keys">{</span>
    <span class="variables">myEvents</span><span class="symbols">.</span><span class="variables">value</span> <span class="keywords">=</span> <span class="variables">myEvents</span><span class="symbols">.</span><span class="variables">value</span><span class="symbols">.</span><span class="functions">filter</span><span class="keys">(</span><span class="keys">(</span><span class="values">event</span><span class="keys">)</span> <span class="keywords">=></span> <span class="values">event</span>.<span class="variables">id</span> <span class="keywords">!==</span> <span class="values">eventId</span><span class="keys">)</span>
  <span class="keys">}</span>

  <span class="directives">return</span> <span class="keys">{</span>
    <span class="functions">addEvent</span>,
    <span class="functions">removeEvent</span>,
  <span class="keys">}</span>
<span class="keys">}</span>
<span class="symbols">&lt;/</span><span class="tags">script</span><span class="symbols">&gt;</span>

<span class="symbols">&lt;</span><span class="tags">style</span> <span class="keywords">lang</span><span class="symbols">="</span>scss<span class="symbols">"</span><span class="symbols">&gt;</span>
<span class="directives">@use</span> <span class="symbols">'</span><span class="strings">@/assets/scss/variables</span><span class="symbols">'</span> <span class="directives">as</span> <span class="variables">vars</span><span class="symbols">;</span>

<span class="comments">/* UI Library */</span>
<span class="tags">body</span> <span class="keys">{</span>
  <span class="properties-types">background-color</span><span class="symbols">:</span> <span class="values">back</span><span class="symbols">;</span>
  <span class="properties-types">font-family</span><span class="symbols">:</span> <span class="symbols">"</span><span class="strings">Segoe UI</span><span class="symbols">"</span>, <span class="values">Tahoma</span><span class="symbols">,</span> <span class="values">Geneva</span><span class="symbols">,</span> <span class="values">Verdana</span><span class="symbols">,</span> <span class="values">sans-serif</span><span class="symbols">;</span>
<span class="keys">}</span>

.<span class="tags">input-styles</span> <span class="keys">{</span>
  <span class="directives">@include</span> <span class="variables">mixins</span><span class="symbols">.</span><span class="functions">ui-control</span><span class="symbols">;</span>
  
  <span class="properties-types">width</span><span class="symbols">:</span> <span class="values">150px</span><span class="symbols">;</span>
  <span class="properties-types">color</span><span class="symbols">:</span> <span class="directives">#bbb</span><span class="symbols">;</span>
<span class="keys">}</span>
<span class="symbols">&lt;/</span><span class="tags">style</span><span class="symbols">&gt;</span>
    </pre>
    <ColorControlPanel
      :colorVars="colorVars"
      @onChangeColor="onChangeColor"
      @onRestoreColor="onRestoreColor"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
import ColorControlPanel from "./components/ColorControlPanel.vue";

const initColorValues = {
  backgroundColor: "#222220",
  tagsColor: "#f9c067",
  symbolsColor: "#bbbbbb",
  variablesColor: "#e6e9f0",
  commentsColor: "#546E7A",
  functionsColor: "#92aadf",
  directivesColor: "#afa691",
  keywordsColor: "#fcc9b2",
  stringsColor: "#89b4c7",
  propertiesTypesColor: "#B2CCD6",
  valuesColor: "#d2a272",
};

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
