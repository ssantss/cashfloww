<template>
  <LayoutVue>
    <template #header> <HeaderVue></HeaderVue> </template>
    <template #resume>
      <IndexVue
        :label="'Ahorro Total'"
        :total-amount="150000"
        :amount="amount"
        :date="date"
      >
        <template #graphic>
          <GraphicVue :amounts="amounts"></GraphicVue
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
      movements: [
        {
          id: 0,
          title: "Movimiento 0",
          description: "Lorem ipsum sit amet",
          amount: 100,
          time: new Date("10-01-2022"),
        },
        {
          id: 1,
          title: "Movimiento 1",
          description: "Lorem ipsum sit amet",
          amount: 200,
          time: new Date("10-01-2022"),
        },
        {
          id: 2,
          title: "Movimiento 2",
          description: "Lorem ipsum sit amet",
          amount: 500,
          time: new Date("10-01-2022"),
        },
        {
          id: 3,
          title: "Movimiento 3",
          description: "Lorem ipsum sit amet",
          amount: 200,
          time: new Date("10-01-2022"),
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: "Lorem ipsum sit amet",
          amount: -400,
          time: new Date("10-01-2022"),
        },
        {
          id: 5,
          title: "Movimiento 5",
          description: "Lorem ipsum sit amet",
          amount: -600,
          time: new Date("10-01-2022"),
        },
        {
          id: 6,
          title: "Movimiento 6",
          description: "Lorem ipsum sit amet",
          amount: -300,
          time: new Date("10-01-2022"),
        },
        {
          id: 7,
          title: "Movimiento 7",
          description: "Lorem ipsum sit amet",
          amount: 0,
          time: new Date("10-01-2022"),
        },
        {
          id: 8,
          title: "Movimiento 7",
          description: "Lorem ipsum sit amet",
          amount: 300,
          time: new Date("09-01-2022"),
        },
        {
          id: 9,
          title: "Movimiento 7",
          description: "Lorem ipsum sit amet",
          amount: 500,
          time: new Date("09-01-2022"),
        },
      ],
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
        const lastMovements = lastDays.slice(0, i);

        return lastMovements.reduce((suma, movement) => {
          return suma + movement;
        }, 0);
      });
    },
  },
  methods: {
    create(movement) {
      this.movements.push(movement);
    },
    remove(id) {
      const index = this.movements.findIndex((m) => m.id === id);
      this.movements.splice(index, 1);
    },
  },
};
</script>
