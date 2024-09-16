<template>
  <div class="app">
    <button @click="fetchMovie">clik</button>
    <div class="content">
      <AppInfo
        :allMuviesCount="movies.length"
        :favouriteMoviesCount="movies.filter((c) => c.favourites).length"
      />
      <div class="search-pen shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
        <Search :updateTermHandler="updateTermHandler" />
        <Filter
          :updateFilterHandler="updateFilterHandler"
          :filterName="filter"
        />
      </div>
      <div class="search-pen shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
        <Move
          :movies="onFilterhandler(onSearchHandler(movies, term), filter)"
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
import axios from "axios";
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
      movies: [],
      term: "",
      filter: "all",
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
    onFilterhandler(arr, filter) {
      switch (filter) {
        case "popular":
          return arr.filter((c) => c.like);
        case "mostViewers":
          return arr.filter((c) => c.viewers > 500);

        default:
          return arr;
      }
    },
    updateTermHandler(term) {
      this.term = term;
    },
    updateFilterHandler(filter) {
      this.filter = filter;
    },
    async fetchMovie() {
      try {
        const { data } = await axios.get(
          "https://jsonplaceholder.typicode.com/posts?_limit=10"
        );
        const newArr = data.map((item) => ({
          id: item.id,
          name: item.title,
          viewers: item.id * 10,
          favourites: false,
          like: false,
        }));
        this.movies = newArr;
      } catch (error) {
        console.log(error.message);
      }
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
