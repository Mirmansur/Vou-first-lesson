<template>
  <div class="app">
    <div class="content">
      <AppInfo
        :allMuviesCount="movies.length"
        :favouriteMoviesCount="movies.filter((c) => c.favourites).length"
      />
      <div class="search-pen shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
        <Search :updateTermHandler="updateTermHandler" />
        <Filter />
      </div>
      <div class="search-pen shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
        <Move
          :movies="onSearchHandler(movies, term)"
          @onToggle="onToggleHandler"
          @onRemove="onRemoveHandler"
        />
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
          id: 1,
        },
        {
          name: "transformeri",
          viewers: 927,
          favourites: false,
          like: false,
          id: 2,
        },
        {
          name: "Shrek",
          viewers: 1100,
          favourites: true,
          like: false,
          id: 3,
        },
      ],
      term: "",
    };
  },
  methods: {
    creatMovie(item) {
      this.movies.push(item);
    },
    onToggleHandler({ id, prop }) {
      this.movies = this.movies.map((item) => {
        if (item.id == id) {
          return { ...item, [prop]: !item[prop] };
        }
        return item;
      });
    },
    onRemoveHandler(id) {
      this.movies = this.movies.filter((item) => item.id !== id);
    },
    onSearchHandler(arr, term) {
      if (term.length == 0) {
        return arr;
      }
      return arr.filter((c) => c.name.toLowerCase().indexOf(term) > -1);
    },
    updateTermHandler(term) {
      this.term = term;
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
