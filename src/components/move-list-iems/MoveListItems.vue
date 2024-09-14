<template>
  <ul>
    <li
      class="list-group-item flex justify-between border-b-slate-900 :last-chaild border-b-none"
    >
      <span class="list-group-itme-label text-xl cursor-pointer w-[550px]"
        >Omar</span
      >
      <input
        type="number"
        class="lits-group-item-label text-xl border-none outline-none text-center"
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
        <i class="fas fa-star"></i>
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
</style>
