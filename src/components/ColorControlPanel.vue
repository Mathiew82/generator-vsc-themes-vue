<template>
  <div class="control-panel">
    <h2>Select theme colors</h2>
    <div
      v-for="([key, colorRef], index) in Object.entries(colorVars)"
      :key="key"
      class="justify-between mt-05"
    >
      <div class="items-center">
        <input
          type="color"
          :id="cleanName(key)"
          :name="cleanName(key)"
          :value="colorRef.value"
          @input="onChangeColor(key, $event)"
        />
        <label :for="cleanName(key)">
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
    <button class="restore-button all">Restore by default</button>
    <button class="generate-code-button">Generate JSON code</button>
  </div>
</template>

<script setup>
const props = defineProps({
  colorVars: {
    type: Object,
    required: true,
  },
});

const emit = defineEmits(["onChangeColor", "onRestoreColor"]);

const cleanName = (key) => key.replace(/Color$/, "");
const capitalize = (word) => word.charAt(0).toUpperCase() + word.slice(1);

const onChangeColor = (contentToChange, event) => {
  emit("onChangeColor", { contentToChange, event });
};

const onRestoreColor = (colorToRestore) => {
  emit("onRestoreColor", colorToRestore);
};
</script>
