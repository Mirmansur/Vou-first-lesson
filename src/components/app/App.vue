<template>
  <div class="app">
    <div class="content">
      <AppInfo />
      <div class="search-pen shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
        <Search />
        <Filter />
      </div>
      <div class="search-pen shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
        <Move />
      </div>
      <div class="search-pen shadow-md bg-[#fcfaf5] p-4 mt-[2rem] rounded-md">
        <MoveForm />
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
