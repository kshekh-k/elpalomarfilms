<script lang="ts">
  const menu = [
    {
      name: "Canada",
      url: "/",
      isActive: true,
    },
    {
      name: "Archive",
      url: "/archive",
      isActive: false,
    },
    {
      name: "Contact",
      url: "/contact",
      isActive: false,
    },
    {
      name: "About",
      url: "/about",
      isActive: false,
    },
  ];

  if (typeof window !== "undefined") {
    menu.forEach(item => {
      item.isActive = window.location.pathname === item.url;
    });
  }
</script>

<header class="grid grid-cols-12 gap-8 px-3 2xlpx-24">
  <div class="col-start-5">
    <nav class="text-menu text-grey">
      <div class="col-span-4 col-start-5 uppercase flex flex-col gap-1">
        {#each menu as item}
          <a
            href={item.url}
            class="pointer-events-auto relative flex gap-1 w-fit items-center text-sm font-medium ease-in-out duration-300 hover:before:opacity-100 hover:after:opacity-100 before:ease-in-out before:duration-300 after:ease-in-out after:duration-300 before:content-['['] after:content-[']'] {item.isActive
              ? 'text-gray-900'
              : 'text-gray-400 hover:text-gray-900 before:opacity-0 after:opacity-0'}"
          >
            {item.name}
          </a>
        {/each}
      </div>
    </nav>
  </div>
</header>
