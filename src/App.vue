<template>
  <div class="app">
    <pre>
<span class="symbols">&lt;</span>template<span class="symbols">&gt;</span>
  <span class="symbols">&lt;</span>input
    v-model="model"
    class="ui-input py-2 px-5 rounded-full text-sm text-white outline-0"
    :class="defaultStyles"
  /<span class="symbols">&gt;</span>
<span class="symbols">&lt;</span>/template<span class="symbols">&gt;</span>

<span class="symbols">&lt;</span>script setup lang="ts"<span class="symbols">&gt;</span>
import { ref } from 'vue'
import { useType } from '~/components/ui/composable/useType'
import type { Event } from '@/types/Event'

const model = defineModel<span class="symbols">&lt;</span>string<span class="symbols">&gt;</span>()

const { defaultStyles } = useType('default')

export const useMyEvents = () => {
  const addEvent = (newEvent: Event): void => {
    myEvents.value.push(newEvent)
  }

  const removeEvent = (eventId: number): void => {
    myEvents.value = myEvents.value.filter((event) => event.id !== eventId)
  }

  return {
    addEvent,
    removeEvent,
  }
}
<span class="symbols">&lt;</span>/script<span class="symbols">&gt;</span>

<span class="symbols">&lt;</span>style lang="scss"<span class="symbols">&gt;</span>
body {
  background-color: black;
  color: #eee;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-size: 16px;
}

.input-styles {
  color: #bbb;
}
<span class="symbols">&lt;</span>/style<span class="symbols">&gt;</span>
    </pre>

    <div class="control-panel">
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
      <div class="items-center mt-1">
        <input
          type="color"
          id="symbols"
          name="symbols"
          :value="symbolsColor"
          @input="onChangeColor('symbolsColor', $event)"
        />
        <label for="symbols">Symbols</label>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const backgroundColor = ref("#222220");
const symbolsColor = ref("#bbb");
const variablesColor = ref("#f00");

const colorVars = {
  backgroundColor,
  symbolsColor,
  variablesColor,
};

const onChangeColor = (contentToChange, event) => {
  colorVars[contentToChange].value = event.target.value;
};
</script>

<style>
.app {
  height: 100vh;
  background-color: v-bind(backgroundColor);
}

.symbols {
  color: v-bind(symbolsColor);
}

.variables {
  color: v-bind(variablesColor);
}
</style>
