<template>
  <div class="app">
    <pre>
<span class="symbols">&lt;</span><span class="tags">template</span><span class="symbols">&gt;</span>
  <span class="symbols">&lt;</span><span class="tags">input</span>
    <span class="keywords">v-model</span><span class="symbols">="</span><span class="variables">model</span><span class="symbols">"</span>
    <span class="keywords">class</span><span class="symbols">="</span>ui-input py-2 px-5 rounded-full text-sm text-white outline-0<span class="symbols">"</span>
    <span class="symbols">:</span><span class="keywords">class</span><span class="symbols">="</span><span class="variables">defaultStyles</span><span class="symbols">"</span>
  <span class="symbols">/&gt;</span>
<span class="symbols">&lt;/</span><span class="tags">template</span><span class="symbols">&gt;</span>

<span class="symbols">&lt;</span><span class="tags">script</span> <span class="keywords">setup lang</span><span class="symbols">="</span>ts<span class="symbols">"</span><span class="symbols">&gt;</span>
<span class="directives">import</span> { <span class="tags">ref</span> } <span class="directives">from</span> <span class="symbols">'</span>vue<span class="symbols">'</span>
<span class="directives">import</span> { <span class="tags">useType</span> } <span class="directives">from</span> <span class="symbols">'</span>~/components/ui/composable/useType<span class="symbols">'</span>
<span class="directives">import type</span> { <span class="tags">Event</span> } <span class="directives">from</span> <span class="symbols">'</span>@/types/Event<span class="symbols">'</span>

<span class="keywords">const</span> <span class="variables">model</span> = <span class="functions">defineModel</span><span class="symbols">&lt;</span>string<span class="symbols">&gt;</span>()

<span class="keywords">const</span> { <span class="variables">defaultStyles</span> } = <span class="functions">useType</span>(<span class="symbols">'</span>default<span class="symbols">'</span>)

<span class="directives">export</span> const <span class="functions">useMyEvents</span> = () => {
  <span class="keywords">const</span> <span class="functions">addEvent</span> <span class="keywords">=</span> (newEvent: Event): void => {
    <span class="variables">myEvents</span>.<span class="variables">value</span>.push(newEvent)
  }

  <span class="keywords">const</span> <span class="functions">removeEvent</span> <span class="keywords">=</span> (eventId: number): void => {
    <span class="variables">myEvents</span>.<span class="variables">value</span> <span class="keywords">=</span> myEvents.value.<span class="functions">filter</span>((event) => event.<span class="variables">id</span> !== eventId)
  }

  <span class="directives">return</span> {
    <span class="functions">addEvent</span>,
    <span class="functions">removeEvent</span>,
  }
}
<span class="symbols">&lt;/</span><span class="tags">script</span><span class="symbols">&gt;</span>

<span class="symbols">&lt;</span><span class="tags">style</span> <span class="keywords">lang</span><span class="symbols">="</span>scss<span class="symbols">"</span><span class="symbols">&gt;</span>
<span class="directives">@use</span> '@/assets/scss/variables' <span class="directives">as</span> <span class="variables">vars</span>;

<span class="comments">/* UI Library */</span>
<span class="tags">body</span> {
  background-color: black;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.<span class="tags">input-styles</span> {
  @include <span class="variables">mixins</span>.ui-control;
  color: #bbb;
}
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
};

const backgroundColor = ref(initColorValues.backgroundColor);
const tagsColor = ref(initColorValues.tagsColor);
const symbolsColor = ref(initColorValues.symbolsColor);
const variablesColor = ref(initColorValues.variablesColor);
const commentsColor = ref(initColorValues.commentsColor);
const functionsColor = ref(initColorValues.functionsColor);
const directivesColor = ref(initColorValues.directivesColor);
const keywordsColor = ref(initColorValues.keywordsColor);

const colorVars = {
  backgroundColor,
  tagsColor,
  symbolsColor,
  variablesColor,
  commentsColor,
  functionsColor,
  directivesColor,
  keywordsColor,
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
</style>
