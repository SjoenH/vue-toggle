<script setup>
import {ref} from 'vue';
import ToggleSwitch from "./ToggleSwitch.vue";

// Define reactive variables for the ToggleSwitch examples
const checked = ref(false);
const checked2 = ref(true);
const checked3 = ref(false);
</script>

<template>
  <h1>ToggleSwitch Component Demo</h1>
  <p>ToggleSwitch is a controlled component that can be used to toggle a boolean value.</p>

  <h2>Example 1: Basic ToggleSwitch</h2>
  <ToggleSwitch v-model:checked="checked" :label-right="checked ? 'On' : 'Off'"/>

  <h2>
    Example 2: ToggleSwitch disabled in different states
  </h2>
  <p>It can be disabled in both states:</p>
  <ToggleSwitch disabled/>
  <ToggleSwitch checked disabled/>

  <h2>Example 3: Using ToggleSwitch with and without labels</h2>
  <p>It can be used with or without labels:</p>
  <p>Note, they switch together because they share the same state to show two-way binding.</p>
  <ToggleSwitch v-model:checked="checked2" labelLeft="Left"/>
  <ToggleSwitch v-model:checked="checked2" labelRight="Right"/>
  <br>
  <ToggleSwitch v-model:checked="checked2" labelLeft="Left" labelRight="Right"/>

  <h2>
    Example 4: Using ToggleSwitch in an uncontrolled form
  </h2>
  <p>
    Check the URL after submitting the form to see the query string change.
  </p>
  <form method="get">
    <ToggleSwitch labelLeft="Subscribe" name="subscribe" checked/>
    <button type="submit">Submit</button>
  </form>

  <h2>
    Example 5: Show transitioning into disabled state
  </h2>
  <p>Press this toggle to see the other toggle switch transition into a disabled state.</p>
  <ToggleSwitch v-model:checked="checked3" label-left="Disable the toggle under"/>
  <ToggleSwitch :disabled="checked3" :label-right="checked3?`Can't touch me!`:`You can interact with me`"/>
</template>

<style>
body {
  font-family: "Helvetica Neue", sans-serif;
}
</style>