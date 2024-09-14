<template>
  <div class="app">
    <div class="content">
      <AppInfo
        :allMuviesCount="movies.length"
        :favouriteMoviesCount="movies.filter((c) => c.favourites).length"
      />
      <div class="search-pen shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
        <Search />
        <Filter />
      </div>
      <div class="search-pen shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
        <Move :movies="movies" />
      </div>
      <div class="search-pen shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
        <MoveForm @creatMovie="creatMovie" />
      </div>
    </div>
  </div>
</template>

<script>
import AppInfo from "@/components/appinfo/AppInfo.vue";
import Search from "@/components/search/Search.vue";
import Filter from "@/components/filter/Filter.vue";
import Move from "@/components/move-list/Move.vue";
import MoveForm from "@/components/move-add-form/MoveForm.vue";

export default {
  components: {
    AppInfo,
    Search,
    Filter,
    Move,
    MoveForm,
  },
  data() {
    return {
      movies: [
        {
          name: "Omar",
          viewers: 811,
          favourites: false,
          like: true,
        },
        {
          name: "transformeri",
          viewers: 927,
          favourites: false,
          like: false,
        },
        {
          name: "Shrek",
          viewers: 1100,
          favourites: true,
          like: false,
        },
      ],
    };
  },
  methods: {
    creatMovie(items) {
      this.movies.push(items);
    },
  },
};
</script>

<style>
.app {
  height: 100vh;
  color: #000;
}
.content {
  width: 1000px;
  min-height: 700px;
  background-color: #fff;
  margin: 0 auto;
  padding: 5rem 0;
}
</style>
