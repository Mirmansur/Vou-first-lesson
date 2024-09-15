<template>
  <div class="btn-group mt-3">
    <button
      v-for="btn in filterButton"
      :key="btn.nmae"
      class="btn"
      :class="[filterName === btn.name ? 'btn-dark' : 'btn-outline-dark']"
      @click="filterHandler(btn.name)"
    >
      {{ btn.title }}
    </button>
  </div>
</template>
<script>
export default {
  props: {
    updateFilterHandler: {
      type: Function,
      required: true,
    },
    filterName: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      filterButton: [
        {
          title: "Barcha kinolar",
          name: "all",
        },
        {
          title: "Mashhur kinolar",
          name: "popular",
        },
        {
          title: "Eng ko'p k'rilgan kinolar",
          name: "mostViewers",
        },
      ],
      filter: "all",
    };
  },
  methods: {
    filterHandler(filter) {
      this.filter = filter;
      this.updateFilterHandler(this.filter);
    },
  },
};
</script>
<style></style>
