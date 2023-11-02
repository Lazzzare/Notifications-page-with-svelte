<script lang="ts">
  // Imports
  import NotificationsHeader from "./NotificationsHeader.svelte";
  import Data from "./../Data.json";
  console.log(Data);

  //   Props
  export let title: string;
  export let markAll: string;
  export let notificationCount: number;
</script>

<main class="box bg-white w-[730px] rounded-none md:rounded-2xl">
  <!-- Props -->
  <NotificationsHeader {title} {markAll} {notificationCount} />
  <!-- Notification Comments -->
  <div class="flex flex-col gap-[10px] px-[30px]">
    {#each Data as item}
      <div
        class={`p-4 flex flex-row items-center rounded-lg gap-3 ${
          item.newPost ? "bg-[#F7FAFD]" : null
        }`}
      >
        <img
          src={item.avatar}
          alt={`${item.user} image`}
          class="w-10 md:w-12"
        />
        <div class="flex flex-col">
          <div class="flex flex-row gap-[6px]">
            <p class="text-sm font-extrabold text-[#1C202B] leading-normal">
              {item.user}
            </p>
            <p class="text-[#5E6778] text-sm font-medium leading-normal inline">
              {item.activity}
            </p>
            <p class="font-bold text-[#5E6778] text-sm leading-normal inline">
              {item.referalPost}
            </p>
            <p>{item.referalGroup}</p>
            {#if item.newPost}
              <!-- <div class="text-[#F65552] w-2 h-2 rounded-full"></div> -->
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="8"
                height="8"
                viewBox="0 0 8 8"
                fill="none"
              >
                <circle cx="4" cy="4" r="4" fill="#F65552" />
              </svg>
            {/if}
          </div>
          <p class="text-sm text-[#939CAD] font-medium leading-normal">
            {item.timestamp}
          </p>
          {#if item.privateText}
            <div class="border-[1px] border-[#DDE7EE] rounded-md bg-white">
              <p class="p-5">{item?.privateText}</p>
            </div>
          {/if}
        </div>
      </div>
    {/each}
  </div>
</main>
