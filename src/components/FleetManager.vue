<template>
  <div class="fleet-manager">
    <div class="list">
      <MachineList @select="showDetails"></MachineList>
    </div>

    <div class="details">
      <h1>Details</h1>
      <h3 v-show="!selectedMachine">No selection</h3>
      <div class="data" v-show="selectedMachine">
        <h2>ID</h2>
        {{ selectedMachine?.id }}
        <h2>Status</h2>
        {{ selectedMachine?.active }}
        <h2>Make & type</h2>
        {{ selectedMachine?.make }} / {{ selectedMachine?.type }}
        <h2>Location</h2>
        N: {{ selectedMachine?.location.N }}<br />
        E: {{ selectedMachine?.location.E }}
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/runtime-core";
import MachineList from "@/components/MachineList.vue";

export default {
  components: { MachineList },
  name: "FleetManager",
  setup() {
    const selectedMachine = ref();
    const showDetails = (machine) => {
      if (selectedMachine && machine.id == selectedMachine.value?.id) {
        selectedMachine.value = null;
        return;
      }
      selectedMachine.value = machine;
    };
    return { selectedMachine, showDetails };
  },
};
</script>

<style scoped>
.fleet-manager {
  display: flex;
  padding: 30px;
  gap: 30px;
  text-align: left;
}

.list,
.details {
  width: 50%;
}
.details {
  padding: 0 30px;
  border-left: 1px solid #aaa;
}

h1 {
  margin: 0;
}
h2 {
  margin-bottom: 10px;
}
h3 {
  font-weight: 400;
  color: #888;
}
</style>
