<template>
  <div class="machine-list">
    <div v-for="machine in machines" :key="machine.id">
      <MachineListCard
        :machine="machine"
        :selected="machine.id === selectedID"
        @select="select"
      ></MachineListCard>
    </div>
  </div>
</template>

<script>
import { ref } from "@vue/runtime-core";
import api from "@/api/mockApi.js";
import MachineListCard from "@/components/MachineListCard.vue";

export default {
  name: "MachineList",
  components: {
    MachineListCard,
  },
  setup(_, ctx) {
    const selectedID = ref();
    const machines = ref(api);
    const select = (machine) => {
      ctx.emit("select", machine);

      if (machine.id == selectedID.value) {
        selectedID.value = null;
        return;
      }
      selectedID.value = machine.id;
    };
    return { machines, selectedID, select };
  },
};
</script>

<style scoped>
.machine-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
</style>
