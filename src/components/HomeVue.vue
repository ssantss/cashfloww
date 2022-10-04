<template>
  <LayoutVue>
    <template #header> <HeaderVue></HeaderVue> </template>
    <template #resume>
      <IndexVue
        :label="'Ahorro Total'"
        :total-amount="totalAmount"
        :amount="amount"
        :date="date"
      >
        <template #graphic>
          <GraphicVue :amounts="amounts" @select="select"></GraphicVue
        ></template>
        <template #action> <actionVue @create="create" /> </template>
      </IndexVue>
    </template>
    <template #movements>
      <MovementsVue :movements="movements" @remove="remove"></MovementsVue>
    </template>
  </LayoutVue>
</template>

<script>
import LayoutVue from "./LayoutVue.vue";
import HeaderVue from "./HeaderVue.vue";
import IndexVue from "./ResumeVue/indexVue.vue";
import MovementsVue from "./MovementsVuee/MovementsVue.vue";
import ActionVue from "./actionVue.vue";
import GraphicVue from "./ResumeVue/GraphicVue.vue";

export default {
  components: {
    LayoutVue,
    HeaderVue,
    IndexVue,
    ActionVue,
    MovementsVue,
    GraphicVue,
  },
  data() {
    return {
      amount: null,
      label: null,
      movements: [],
    };
  },
  computed: {
    amounts() {
      const lastDays = this.movements
        .filter((m) => {
          const today = new Date();
          const oldDate = today.setDate(today.getDate() - 30);
          return m.time >= oldDate;
        })
        .map((m) => m.amount);
      return lastDays.map((m, i) => {
        const lastMovements = lastDays.slice(0, i + 1);

        return lastMovements.reduce((suma, movement) => {
          return suma + movement;
        }, 0);
      });
    },
    totalAmount() {
      return this.movements.reduce((suma, m) => {
        return suma + m.amount;
      }, 0);
    },
  },
  mounted() {
    const movements = JSON.parse(localStorage.getItem("movements"));

    if (Array.isArray(movements)) {
      this.movements = movements.map((m) => {
        return { ...m, time: new Date(m.time) };
      });
    }
  },
  methods: {
    create(movement) {
      this.movements.push(movement);
      this.save();
    },
    remove(id) {
      const index = this.movements.findIndex((m) => m.id === id);
      this.movements.splice(index, 1);
      this.save();
    },
    save() {
      localStorage.setItem("movements", JSON.stringify(this.movements));
    },
    select(el) {
      this.amount = el;
    },
  },
};
</script>
