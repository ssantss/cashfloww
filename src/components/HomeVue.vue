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
        <template #action>action</template>
      </IndexVue>
    </template>
  </LayoutVue>
</template>

<script>
import LayoutVue from "./LayoutVue.vue";
import HeaderVue from "./HeaderVue.vue";
import IndexVue from "./ResumeVue/indexVue.vue";

export default {
  components: {
    LayoutVue,
    HeaderVue,
    IndexVue,
  },
  data() {
    return {
      amount: null,
      date: "25/05/2022",
    };
  },
};
</script>
