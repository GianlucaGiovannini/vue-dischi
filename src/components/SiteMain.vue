<template>
  <main>
      <SelectGender v-model="selectValue" @select="change" />
      <DiscList />
  </main>
</template>

<script>
import DiscList from "@/components/DiscListComponent.vue"
import SelectGender from "@/components/SelectGenderComponent.vue"
import state from '@/state.js';

export default {
  name: "SiteMain",
  components: {
      DiscList,
      SelectGender
  },
  data() {
    return {
      selectValue: "all"
    }
  },
  methods: {
    change(){
      console.log(this.selectValue)
      this.
      state.selectValue = this.selectValue;
    }
  },
};
</script>

<style lang="scss" scoped>
</style>