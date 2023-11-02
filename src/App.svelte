<script lang="ts">
  import NotificationsBox from "./lib/NotificationsBox.svelte";

  let notificationCount = 3;
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
