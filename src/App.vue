<template>
  <Beverage :isIced="currentTemp === 'Cold'" />
  <div class="base-options">
    <ul>
      <li>
        <template v-for="base in bases" :key="base.id">
          <label>
            <input
              type="radio"
              name="base_selection"
              :id="`r${base.name}`"
              :value="base.name"
              v-model="selectedBase"
            />
            {{ base.name }}
          </label>
        </template>
      </li>
    </ul>
  </div>
  <div>
    <ul>
      <li>
        <template v-for="cream in creamers" :key="cream.id">
          <label>
            <input
              type="radio"
              name="cream_selection"
              :id="`r${cream.name}`"
              :value="cream.name"
              v-model="selectedCreamer"
            />
            {{ cream.name }}
          </label>
        </template>
      </li>
    </ul>
  </div>
  <div>
    <ul>
      <li>
        <template v-for="syrup in syrups" :key="syrup.id">
          <label>
            <input
              type="radio"
              name="syrup_selection"
              :id="`r${syrup.name}`"
              :value="syrup.name"
              v-model="selectedSyrup"
            />
            {{ syrup.name }}
          </label>
        </template>
      </li>
    </ul>
  </div>
  <div>
    <ul>
      <li>
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Beverage from "./components/Beverage.vue";
import { temps, currentTemp } from "./stores/beverage";
import { bases } from "./stores/beverage";
import { creamers } from "./stores/beverage";
import { syrups } from "./stores/beverage";
const selectedBase = ref("");
const selectedCreamer = ref("");
const selectedSyrup = ref("");
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
</style>
