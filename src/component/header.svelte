<script lang="ts">
  const menu = [
    {
      name: "Canada",
      url: "/",
    },
    {
      name: "Archive",
      url: "/",
    },
    {
      name: "Contact",
      url: "/",
    },
    {
      name: "About",
      url: "/",
    },
    {
      name: "Goods",
      url: "/",
    },
  ];
</script>

<header class="grid grid-cols-12 gap-8 px-24">
  <div class="col-start-5">
    <nav class="text-menu text-grey">
      <div class="col-span-4 col-start-5 uppercase flex flex-col gap-1">
        {#each menu as item}
          <a
            href="/"
            class="pointer-events-auto relative flex gap-1 w-fit items-center text-sm font-medium text-gray-400 ease-in-out duration-300 hover:text-gray-900 before:opacity-0 after:opacity-0 hover:before:opacity-100 hover:after:opacity-100 before:ease-in-out before:duration-300 after:ease-in-out after:duration-300 before:content-['['] after:content-[']']"
          >
            {item.name}
          </a>
        {/each}
      </div>
    </nav>
  </div>
</header>
