<script lang="ts">
  // Imports
  import NotificationsHeader from "./NotificationsHeader.svelte";
  import Data from "./../Data.json";

  // Props
  export let title: string;
  export let markAll: string;
  export let notificationCount: number;

  // States
  let clickedItems = new Set();

  const handleItemClick = (item: { newPost: boolean }) => {
    if (item.newPost && !clickedItems.has(item)) {
      clickedItems.add(item);
      notificationCount = notificationCount - 1;
    }
  };

  const handleMarkAllClick = () => {
    notificationCount = 0;
    clickedItems.clear();
  };

  $: console.log(notificationCount);
</script>

<main class="box bg-white rounded-none md:rounded-2xl">
  <!-- Props -->
  <NotificationsHeader
    {title}
    {markAll}
    {notificationCount}
    {handleMarkAllClick}
  />
  <!-- Notification Comments -->
  <div class="flex flex-col gap-[8px] px-[30px]">
    {#each Data as item}
      <!-- svelte-ignore a11y-click-events-have-key-events -->
      <!-- svelte-ignore a11y-no-static-element-interactions -->
      <div
        on:click={() => handleItemClick(item)}
        class={`flex flex-row gap-3 items-start px-5 py-[18px] ${
          clickedItems.has(item)
            ? "bg-white rounded-lg"
            : item.newPost && notificationCount > 0
            ? "bg-[#F7FAFD] rounded-lg cursor-pointer"
            : null
        }`}
      >
        <div>
          <img src={item.avatar} alt={`${item.user} image`} class="w-12 h-12" />
        </div>
        <div class={`flex flex-col`}>
          <h1 class="flex items-center flex-row gap-1">
            <strong
              class="text-base font-extrabold leading-normal hover:text-[#0A327B] transition-all duration-300 cursor-pointer"
            >
              {item.user}
            </strong>
            <p class="text-[#5E6778] text-base font-medium">
              {item.activity}
            </p>
            <p class="text-[#5E6778] text-base font-extrabold">
              {item.referalPost}
            </p>
            <p class="text-[#0A327B] text-base font-extrabold leading-normal">
              {item.referalGroup}
            </p>
            {#if item.newPost}
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
          </h1>
          <span class="text-[#939CAD] text-base font-medium leading-normal"
            >{item.timestamp}</span
          >
          {#if item.privateText}
            <div
              class="mt-3 hover:bg-[#E5EFFA] transition-all duration-300 cursor-pointer"
            >
              <p
                class="w-[526px] p-5 rounded-lg border border-[#DDE7EE] hover:text-[#5E6778] transition-all duration-300"
              >
                {item.privateText}
              </p>
            </div>
          {/if}
        </div>
      </div>
    {/each}
  </div>
</main>
