<template>
  <div class="move-add-form">
    <h1 class="text-2xl font-medium mb-3">Move-form</h1>
    <form class="add-form flex gap-2 items-center" @submit.prevent>
      <input
        type="text"
        placeholder="Qanday  kino ?"
        class="form-control now-movie-label p-1"
        :value="name"
        @input="name = $event.target.value"
      />
      <input
        type="number"
        placeholder="Nechi marotaba ko'rilgan"
        class="form-control now-movie-label"
        :value="viewers"
        @input="viewers = $event.target.value"
      />
      <button type="submit" class="btn btn-outline-dark" @click="addMovie">
        Qo'shish
      </button>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      name: "",
      viewers: "",
    };
  },
  methods: {
    addMovie() {
      if (!this.name || !this.viewers) return;
      const newMovie = {
        name: this.name,
        viewers: this.viewers,
        favourites: false,
        like: false,
        id: Date.now(),
      };
      this.$emit("creatMovie", newMovie);
      (thi.name = ""), (this.viewers = "");
    },
  },
};
</script>
<style></style>
