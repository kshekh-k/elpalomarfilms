<script lang="ts">
  const menu = [
    {
      name: "Home",
      url: "home",
      isActive: true,
    },
    {
      name: "About Us",
      url: "about",
      isActive: false,
    },
    {
      name: "Contact",
      url: "contact",
      isActive: false,
    },
  ];

  if (typeof window !== "undefined") {
    menu.forEach(item => {
      item.isActive = window.location.pathname === item.url;
    });
  }
  export let activeSection: string = "home";
</script>

<header
  class="flex md:grid md:grid-cols-12 gap-8 p-3 2xl:px-24 top-0 fixed bg-white z-50 inset-x-0"
>
  <div class="col-start-4 flex justify-center">
    <a href="/">
      <img
        src="/images/logo-El-Palomar-FIilms-symbol.svg"
        class="w-20"
        alt="El Palomar FIilms"
      />
    </a>
  </div>
  <div class="col-start-5">
    <nav class="text-menu text-grey">
      <div class="col-span-4 col-start-5 uppercase flex flex-col gap-1">
        {#each menu as item}
          <a
            href={`#${item.url}`}
            class="pointer-events-auto relative flex gap-1 w-fit items-center font-medium ease-in-out duration-300 text-gray-900 hover:text-gray-400"
          >
            <span class="italic">{item.name}</span>
          </a>
        {/each}
      </div>
    </nav>
  </div>
</header>
