<template>
  <Beverage 
  :isIced="currentTemp === 'Cold'"
  :base="selectedBase"
  :creamer="selectedCreamer"
  :syrup="selectedSyrup"
  :baseColor="baseColor"
  :creamerColor="creamerColor"
  :syrupColor="syrupColor" />
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
import { temps, currentTemp, bases, creamers, syrups } from "./stores/beverage";
import { computed } from "vue";

const selectedBase = ref(bases.value[0].name);
const selectedCreamer = ref(creamers.value[0].name);
const selectedSyrup = ref(syrups.value[0].name);

const baseColor = computed(() => bases.value.find(b => b.name === selectedBase.value)?.color ?? "transparent");
const creamerColor = computed(() => creamers.value.find(c => c.name === selectedCreamer.value)?.color ?? "transparent");
const syrupColor = computed(() => {const syrup = syrups.value.find(s => s.name === selectedSyrup.value) 
if (!syrup || syrup.name === "No Syrup") { return baseColor.value}
return syrup.color });

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
