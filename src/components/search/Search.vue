<template lang="">
  <input
    type="text"
    class="form-control search-input p-3"
    placeholder="Kinilarni  qidirish"
    @input="changeHandler"
  />
</template>
<script>
export default {
  props: {
    updateTermHandler: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      term: "",
    };
  },
  methods: {
    changeHandler(e) {
      this.term = e.target.value;
      this.updateTermHandler(this.term);
    },
  },
};
</script>
<style lang=""></style>
