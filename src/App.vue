<template>
  <div class="app">
    <pre>
<span class="symbols">&lt;</span><span class="tags">template</span><span class="symbols">&gt;</span>
  <span class="symbols">&lt;</span><span class="tags">input</span>
    v-model="<span class="variables">model</span>"
    class="ui-input py-2 px-5 rounded-full text-sm text-white outline-0"
    :class="<span class="variables">defaultStyles</span>"
  <span class="symbols">/&gt;</span>
<span class="symbols">&lt;/</span><span class="tags">template</span><span class="symbols">&gt;</span>

<span class="symbols">&lt;</span><span class="tags">script</span> setup lang="ts"<span class="symbols">&gt;</span>
import { <span class="tags">ref</span> } from 'vue'
import { <span class="tags">useType</span> } from '~/components/ui/composable/useType'
import type { <span class="tags">Event</span> } from '@/types/Event'

const <span class="variables">model</span> = defineModel<span class="symbols">&lt;</span>string<span class="symbols">&gt;</span>()

const { <span class="variables">defaultStyles</span> } = useType('default')

export const useMyEvents = () => {
  const addEvent = (newEvent: Event): void => {
    <span class="variables">myEvents</span>.<span class="variables">value</span>.push(newEvent)
  }

  const removeEvent = (eventId: number): void => {
    <span class="variables">myEvents</span>.<span class="variables">value</span> = myEvents.value.filter((event) => event.<span class="variables">id</span> !== eventId)
  }

  return {
    addEvent,
    removeEvent,
  }
}
<span class="symbols">&lt;/</span><span class="tags">script</span><span class="symbols">&gt;</span>

<span class="symbols">&lt;</span><span class="tags">style</span> lang="scss"<span class="symbols">&gt;</span>
@use '@/assets/scss/variables' as <span class="variables">vars</span>;

<span class="comments">/* UI Library */</span>
<span class="tags">body</span> {
  background-color: black;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.<span class="tags">input-styles</span> {
  color: #bbb;
}
<span class="symbols">&lt;/</span><span class="tags">style</span><span class="symbols">&gt;</span>
    </pre>

    <div class="control-panel">
      <h2>Select theme colors</h2>
      <div class="justify-between">
        <div class="items-center">
          <input
            type="color"
            id="background"
            name="background"
            :value="backgroundColor"
            @input="onChangeColor('backgroundColor', $event)"
          />
          <label for="background">Background</label>
        </div>
        <div class="items-center">
          <button
            class="restore-button"
            @click="onRestoreColor('backgroundColor')"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="#ffffff"
              class="size-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M6 18 18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>
      <div class="justify-between mt-1">
        <div class="items-center">
          <input
            type="color"
            id="tags"
            name="tags"
            :value="tagsColor"
            @input="onChangeColor('tagsColor', $event)"
          />
          <label for="tags">Tags</label>
        </div>
        <div class="items-center">
          <button class="restore-button" @click="onRestoreColor('tagsColor')">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="#ffffff"
              class="size-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M6 18 18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>
      <div class="justify-between mt-1">
        <div class="items-center">
          <input
            type="color"
            id="symbols"
            name="symbols"
            :value="symbolsColor"
            @input="onChangeColor('symbolsColor', $event)"
          />
          <label for="symbols">Symbols</label>
        </div>
        <div class="items-center">
          <button
            class="restore-button"
            @click="onRestoreColor('symbolsColor')"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="#ffffff"
              class="size-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M6 18 18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>
      <div class="justify-between mt-1">
        <div class="items-center">
          <input
            type="color"
            id="variables"
            name="variables"
            :value="variablesColor"
            @input="onChangeColor('variablesColor', $event)"
          />
          <label for="variables">Variables</label>
        </div>
        <div class="items-center">
          <button
            class="restore-button"
            @click="onRestoreColor('variablesColor')"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="#ffffff"
              class="size-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M6 18 18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>
      <div class="justify-between mt-1">
        <div class="items-center">
          <input
            type="color"
            id="comments"
            name="comments"
            :value="commentsColor"
            @input="onChangeColor('commentsColor', $event)"
          />
          <label for="comments">Comments</label>
        </div>
        <div class="items-center">
          <button
            class="restore-button"
            @click="onRestoreColor('commentsColor')"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke-width="1.5"
              stroke="#ffffff"
              class="size-6"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                d="M6 18 18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>
      <button class="restore-button all">Restore all</button>
      <button class="generate-code-button">Generate code</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const initColorValues = {
  backgroundColor: "#222220",
  tagsColor: "#f9c067",
  symbolsColor: "#bbbbbb",
  variablesColor: "#e6e9f0",
  commentsColor: "#546E7A",
};

const backgroundColor = ref(initColorValues.backgroundColor);
const tagsColor = ref(initColorValues.tagsColor);
const symbolsColor = ref(initColorValues.symbolsColor);
const variablesColor = ref(initColorValues.variablesColor);
const commentsColor = ref(initColorValues.commentsColor);

const colorVars = {
  backgroundColor,
  tagsColor,
  symbolsColor,
  variablesColor,
  commentsColor,
};

const onChangeColor = (contentToChange, event) => {
  colorVars[contentToChange].value = event.target.value;
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
  background-color: #555555;
  border: none;
  border-radius: 3px;
  color: white;
  cursor: pointer;
  font-size: 11px;
  margin-top: 2px;
  padding: 4px;
}
.restore-button:hover {
  background-color: #777777;
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
  background-color: black;
  border: none;
  border-radius: 8px;
  color: white;
  cursor: pointer;
  margin-top: 1em;
  padding: 0.8em 1em;
}
.generate-code-button:hover {
  background-color: #333333;
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
</style>
