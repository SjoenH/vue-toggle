<script setup>
defineProps({
  labelLeft: String,
  labelRight: String,
  checked: Boolean,
  disabled: Boolean,
  name: String
});
const emit = defineEmits(['update:checked']);
const uniqueID = `checkbox-${Math.random().toString(36).substring(2, 7)}`; // To make sure the labels point to the correct input in case you want to click on the label to toggle the checkbox
</script>

<template>
  <div class="toggleContainer">
    <label v-if="labelLeft" :for="uniqueID" class="toggleContainer__label">
      {{ labelLeft }}
    </label>
    <input
        class="toggleContainer__input"
        :id="uniqueID"
        type="checkbox"
        :checked="checked"
        @click="emit('update:checked', $event.target.checked)"
        :disabled="disabled"
        :name="name"
    />
    <label v-if="labelRight" :for="uniqueID" class="toggleContainer__label">
      {{ labelRight }}
    </label>
  </div>
</template>

<style scoped>
.toggleContainer {
  display: flex;
  align-items: center;
  gap: 0.25rem;
}

.toggleContainer__label {
  font-size: 0.875rem;
}

/* the switch - the box around the slider */
.toggleContainer__input {
  position: relative;

  width: 2.125rem;
  height: 1rem;
  border-radius: 1.25rem;
  background-color: rgba(0, 0, 0, 0.2);
  cursor: pointer;

  /* remove default */
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;

  /* animation */
  transition: background-color 0.2s ease;

  &:checked {
    background-color: #518D6C;
  }

  &:disabled {
    cursor: not-allowed;
    background-color: #0000001A;
  }

  &:disabled:checked {
    background-color: rgba(81, 141, 108, 0.5);
  }

  /* using a pseudo-element to create the dot so we don't interfere with events*/
  &::before {
    content: "";
    width: 0.5rem;
    height: 0.5rem;
    border-radius: 0.5rem;
    background-color: #fff;
    position: absolute;
    transition: transform 0.2s ease, width 0.2s ease-in-out, height 0.2s ease; /* ease-in-out on the width adds a bit of fun */

    top: 0.25rem;
    left: 0.25rem;
  }

  &:checked::before {
    transform: translate(1rem, -0.125rem);
    width: 0.75rem;
    height: 0.75rem;
  }
}
</style>
