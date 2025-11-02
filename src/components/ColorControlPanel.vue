<template>
  <div class="control-panel">
    <h2>Select theme colors</h2>
    <div
      v-for="([key, colorRef], index) in Object.entries(colorVars)"
      :key="key"
      class="justify-between mt-05"
    >
      <div class="items-center flex-1">
        <input
          type="color"
          :id="cleanName(key)"
          :name="cleanName(key)"
          :value="colorRef.value"
          @input="onChangeColor(key, $event)"
        />
        <label :for="cleanName(key)" class="flex-1">
          {{ capitalize(cleanName(key)) }}
        </label>
      </div>

      <div class="items-center">
        <button class="restore-button" @click="onRestoreColor(key)">
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
    <button class="restore-button all" @click="onRestoreColors">
      Restore by default
    </button>
    <button class="generate-code-button" @click="onGenerateJsonCode">
      Generate JSON code
    </button>
  </div>
</template>

<script setup>
const props = defineProps({
  colorVars: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits([
  "onChangeColor",
  "onRestoreColor",
  "onRestoreColors",
]);

const cleanName = (key) => key.replace(/Color$/, "");
const capitalize = (word) => word.charAt(0).toUpperCase() + word.slice(1);

const onChangeColor = (contentToChange, event) => {
  emit("onChangeColor", { contentToChange, event });
};

const onRestoreColor = (colorToRestore) => {
  emit("onRestoreColor", colorToRestore);
};

const onRestoreColors = () => {
  emit("onRestoreColors");
};

const onGenerateJsonCode = () => {
  // TODO:
};
</script>

<style>
:root {
  --restore-color: #773333;
  --restore-hover-color: #995555;
  --generate-code-color: #224455;
  --generate-code-hover-color: #446677;
}

.control-panel {
  width: 250px;
  background-color: #f0f0f0;
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
  background-color: var(--restore-color);
  border: none;
  border-radius: 3px;
  color: white;
  cursor: pointer;
  font-size: 11px;
  margin-top: 2px;
  padding: 4px;
}
.restore-button:hover {
  background-color: var(--restore-hover-color);
}
.restore-button.all {
  width: 100%;
  border-radius: 6px;
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
  background-color: var(--generate-code-color);
  border: none;
  border-radius: 6px;
  color: white;
  cursor: pointer;
  margin-top: 1em;
  padding: 0.8em 1em;
}
.generate-code-button:hover {
  background-color: var(--generate-code-hover-color);
}
</style>
