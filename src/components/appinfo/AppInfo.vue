<template>
  <div class="app-info shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
    <p class="text-2xl font-medium mb-2">
      Barcha kinolar soni: {{ allMuviesCount }}
    </p>
    <p class="text-2xl font-medium">
      Ko'rilgan kinolar soni: {{ favouriteMoviesCount }}
    </p>
  </div>
</template>

<script>
export default {
  props: {
    allMuviesCount: {
      type: Number,
      required: true,
    },
    favouriteMoviesCount: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style></style>
