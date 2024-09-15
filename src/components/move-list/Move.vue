<template lang="">
  <ul class="list-group">
    <MoveListItems
      v-for="movie in movies"
      :key="movie.id"
      :movie="movie"
      @onToggle="$emit('onToggle', $event)"
      @onRemove="$emit('onRemove', $event)"
    />
  </ul>
</template>
<script>
import MoveListItems from "@/components/move-list-iems/MoveListItems.vue";
export default {
  components: { MoveListItems },
  props: {
    movies: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style lang=""></style>
