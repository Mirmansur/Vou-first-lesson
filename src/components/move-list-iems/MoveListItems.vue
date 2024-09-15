<template>
  <ul>
    <li
      class="list-group-item flex justify-between border-b-slate-900"
      :class="[{ like: movie.like }, { favourites: movie.favourites }]"
    >
      <span
        @click="$emit('onToggle', { id: movie.id, prop: 'like' })"
        class="label text-xl cursor-pointer w-[550px]"
        >{{ movie.name }}</span
      >
      <input
        type="number"
        class="lits-group-item-input text-xl border-none outline-none text-center"
        :value="movie.viewers"
      />
      <div class="flex justify-center items-center">
        <button
          type="button"
          class="btn-cookie btn-sm w-[35px] h-[35px] m-1 border-none bg-zinc-300 rounded-md text-xl text-center"
          @click="$emit('onToggle', { id: movie.id, prop: 'favourites' })"
        >
          <i class="fas fa-cookie text-[#e09f3e]"></i>
        </button>
        <button
          type="button"
          class="btn-trash btn-sm w-[35px] h-[35px] m-1 border-none bg-zinc-300 rounded-md text-xl text-center"
          @click="$emit('onRemove', movie.id)"
        >
          <i class="fas fa-trash text-[#e5383b]"></i>
        </button>
        <i
          class="fas fa-star w-[35px] h-[35px] text-center text-xl text-[#ffd700]"
        ></i>
      </div>
    </li>
  </ul>
</template>
<script>
export default {
  props: {
    movie: {
      type: Object,
      required: true,
    },
  },
  methods: {
    onLike() {
      this.$emit("onLike", this.movie.id);
    },
  },
};
</script>
<style scoped>
.list-group-item:last-child {
  border-bottom: none;
}
.list-group-item .fa-star {
  transition: 0.3s all;
  transform: translate(30px);
  opacity: 0;
}
.list-group-item.like .fa-star {
  opacity: 1;
  transform: translate(0);
}
.list-group-item.favourute .label {
  color: #e09f3e;
}
.list-group-item.favourute .lits-group-item-input {
  color: #e09f3e;
}
</style>
