<template>
  <LayoutVue>
    <template #header> <HeaderVue></HeaderVue> </template>
    <template #resume>
      <IndexVue :label="'Ahorro Total'" :amount="10000" />
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
};
</script>
