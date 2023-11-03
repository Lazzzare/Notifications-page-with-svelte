<script lang="ts">
  export let title: string;
  export let markAll: string;
  export let notificationCount: number;
</script>

<main
  class="px-4 py-6 md:p-8 w-full flex flex-row items-center justify-between"
>
  <div class="flex flex-row items-center gap-2 md:gap-3">
    <h1 class="text-xl font-extrabold leading-normal text-[#1C202B]">
      {title}
    </h1>
    <div
      class="text-white font-extrabold leading-normal py-[1px] px-[11px] bg-[#0A327B] rounded-md"
    >
      {notificationCount}
    </div>
  </div>
  <h2
    class="text-base font-medium leading-normal text-[#5E6778] cursor-pointer hover:text-[#0A327B] transition-all duration-300"
  >
    {markAll}
  </h2>
</main>
