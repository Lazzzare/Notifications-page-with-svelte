<script lang="ts">
  import NotificationsBox from "./lib/NotificationsBox.svelte";
  import Data from "./Data.json";

  let notificationCount = Data.filter((item) => item.newPost).length;
</script>

<main
  class="w-full h-screen bg-[#F9FAFD] flex justify-center md:items-center items-start"
>
  <NotificationsBox
    title="Notifications"
    markAll="Mark all as read"
    {notificationCount}
  />
</main>
