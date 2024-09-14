<template>
  <ul>
    <li class="list-group-item flex justify-between border-b-slate-900">
      <span class="list-group-itme-label text-xl cursor-pointer w-[550px]"
        >Omar</span
      >
      <input
        type="number"
        class="lits-group-item-input text-xl border-none outline-none text-center"
        defaultValue="811"
      />
      <div class="flex justify-center items-center">
        <butto
          type="button"
          class="btn-cookie btn-sm w-[35px] h-[35px] m-1 border-none bg-zinc-300 rounded-md text-xl text-center"
          ><i class="fas fa-cookie text-[#e09f3e]"></i
        ></butto>
        <butto
          type="button"
          class="btn-trash btn-sm w-[35px] h-[35px] m-1 border-none bg-zinc-300 rounded-md text-xl text-center"
          ><i class="fas fa-trash text-[#e5383b]"></i
        ></butto>
        <i
          class="fas fa-star w-[35px] h-[35px] text-center text-xl text-[#ffd700]"
        ></i>
      </div>
    </li>
  </ul>
</template>
<script>
export default {};
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
.list-group-item.favourute .lits-group-item-label,
.list-group-item.favourute .lits-group-item-input {
  color: #e09f3e;
}
</style>
