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
        <template #graphic> graphic</template>
        <template #action> <ActionVue></ActionVue> </template>
      </IndexVue>
    </template>
    <template #movements>
      <MovementsVue :movements="movements"></MovementsVue>
    </template>
  </LayoutVue>
</template>

<script>
import LayoutVue from "./LayoutVue.vue";
import HeaderVue from "./HeaderVue.vue";
import IndexVue from "./ResumeVue/indexVue.vue";
import MovementsVue from "./MovementsVuee/MovementsVue.vue";
import ActionVue from "./actionVue.vue";

export default {
  components: {
    LayoutVue,
    HeaderVue,
    IndexVue,
    ActionVue,
    MovementsVue,
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
          amount: 1000,
        },
        {
          id: 1,
          title: "Movimiento 1",
          description: "Lorem ipsum sit amet",
          amount: 1000,
        },
        {
          id: 2,
          title: "Movimiento 2",
          description: "Lorem ipsum sit amet",
          amount: 1000,
        },
        {
          id: 3,
          title: "Movimiento 3",
          description: "Lorem ipsum sit amet",
          amount: 1000,
        },
        {
          id: 4,
          title: "Movimiento 4",
          description: "Lorem ipsum sit amet",
          amount: 1000,
        },
        {
          id: 5,
          title: "Movimiento 5",
          description: "Lorem ipsum sit amet",
          amount: 1000,
        },
        {
          id: 6,
          title: "Movimiento 6",
          description: "Lorem ipsum sit amet",
          amount: 1000,
        },
        {
          id: 7,
          title: "Movimiento 7",
          description: "Lorem ipsum sit amet",
          amount: 1000,
        },
      ],
    };
  },
};
</script>
