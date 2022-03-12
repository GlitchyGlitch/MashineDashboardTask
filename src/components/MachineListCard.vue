<template>
  <div :class="['machine-list-card', { selected: selected }]">
    <div :class="['active-indicator', { 'is-active': machine.active }]">
      <div>{{ indicatorText }}</div>
    </div>
    <div class="data" @click="select">
      <h1 class="make">
        {{ machine.make }}<span class="id">#{{ machine.id }}</span>
      </h1>
      <h3 class="type">{{ machine.type }}</h3>
    </div>
  </div>
</template>

<script>
import { computed } from "@vue/runtime-core";
export default {
  name: "MachineListCard",
  props: {
    id: {
      require: true,
      type: Number,
    },
    machine: {
      require: true,
      type: Object,
    },
    selected: {
      default: false,
      type: Boolean,
    },
  },

  setup(props, ctx) {
    const indicatorText = computed(() => {
      if (props.machine.active) {
        return "Active";
      }
      return "Inactive";
    });

    const select = () => {
      ctx.emit("select", props.machine);
    };
    return { indicatorText, select };
  },
};
</script>

<style scoped>
.machine-list-card {
  text-align: left;
  display: flex;
  width: 100%;
}
.machine-list-card.selected {
  background-color: #2c3e5026;
}
.data {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin-left: 15px;
  padding: 10px;
  cursor: pointer;
}
.make {
  margin: 0;
  display: block;
}
.type {
  display: block;
  margin: 0;
  text-transform: capitalize;
  font-weight: 400;
  color: #888;
}
.id {
  color: #888;
}
.active-indicator {
  width: 30px;
  background-color: #a10000;
  writing-mode: vertical-rl;
  text-align: center;
  color: #fff;
  display: grid;
  place-items: center;
}
.active-indicator.is-active {
  background-color: #008509;
}
</style>
