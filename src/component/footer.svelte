<script lang="ts">
  const socialmedia = [
    {
      label: "Instagram",
      url: "/",
    },
    {
      label: "Twitter",
      url: "/",
    },
    {
      label: "LinkedIn",
      url: "/",
    },
    {
      label: "Facebook",
      url: "/",
    },
  ];
</script>

<footer class="flex flex-col md:grid grid-cols-12 gap-8 px-3 2xl:px-24 pt-10">
  <div class="max-w-40">
    <img src="/images/Logo-El-Palomar-FIilms.svg" alt="El Palomar FIilms" />
  </div>
  <div class="col-span-full grid gap-8 sm:col-span-5 sm:col-start-3">
    <div class="grid grid-cols-5 gap-4 sm:gap-8">
      <h3
        class="col-span-full sm:col-span-2 sm:justify-self-end uppercase text-sm font-medium"
      >
        Barcelona (HQ)
      </h3>
      <div class="col-span-3">
        <p class="text-sm font-medium">
          Almogàvers 68-70, 9º<br />Barcelona, Spain 08018<br />+34 93 356 84 83<br
          /><a
            href="/#"
            class="hover:text-gray-400 text-gray-900 ease-in-out duration-300"
            >info@canadacanada.com</a
          >
        </p>
      </div>
    </div>
    <div class="grid grid-cols-5 gap-4 sm:gap-8">
      <h3
        class="col-span-full sm:col-span-2 sm:justify-self-end uppercase text-sm font-medium"
      >
        London
      </h3>
      <div class="col-span-3">
        <p class="text-sm font-medium">
          1, Waterside<br />44-48 Wharf Rd<br />London N1 7UX<br />+44 203 371
          7652<br /><a
            href="/#"
            class="hover:text-gray-400 text-gray-900 ease-in-out duration-300"
            >london@canadacanada.com</a
          >
        </p>
      </div>
    </div>
    <div class="grid grid-cols-5 gap-4 sm:gap-8">
      <h3
        class="col-span-full sm:col-span-2 sm:justify-self-end uppercase text-sm font-medium"
      >
        Los Angeles
      </h3>
      <div class="col-span-3">
        <p class="text-sm font-medium">
          8440 Warner Dr, STE A2, Culver City, CA 90232<br />+1 (310) 7524350<br
          /><a
            href="/#"
            class="hover:text-gray-400 text-gray-900 ease-in-out duration-300"
            >losangeles@canadacanada.com</a
          ><br />&nbsp;
        </p>
      </div>
    </div>
    <div class="grid grid-cols-5 gap-4 sm:gap-8">
      <h3
        class="col-span-full sm:col-span-2 sm:justify-self-end uppercase text-sm font-medium"
      >
        Shop Enquiries
      </h3>
      <div class="col-span-3">
        <p class="text-sm font-medium">
          <a
            href="/#"
            class="hover:text-gray-400 text-gray-900 ease-in-out duration-300"
            >shop@canadacanada.com</a
          >
        </p>
      </div>
    </div>
  </div>
  <div class="col-span-full flex flex-col gap-12 sm:col-span-3 sm:col-start-10">
    <div class="flex flex-col gap-2 text-sm uppercase">
      {#each socialmedia as item}
        <a
          href={item.url}
          target="_blank"
          rel="noopener noreferrer"
          class="pointer-events-auto relative flex w-fit items-center text-gray-400 hover:text-gray-900 ease-in-out duration-300"
        >
          {item.label}
        </a>
      {/each}
    </div>
    <form action="" class="flex flex-wrap gap-2" method="POST">
      <label for="newsletter_email" class="w-full text-sm font-medium"
        >Subscribe to our newsletter</label
      >
      <div class="flex w-full">
        <input
          class="w-full outline-none py-1 text-sm uppercase text-gray-600 hover:text-gray-900 ease-in-out duration-300"
          type="email"
          name="email"
          id="newsletter_email"
          placeholder="Email"
        />
        <button
          type="submit"
          class="button relative h-8 overflow-visible py-0 text-center leading-none cursor-pointer uppercase text-sm font-medium text-gray-400 hover:text-gray-900 ease-in-out duration-300 before:opacity-0 after:opacity-0 hover:before:opacity-100 hover:after:opacity-100 before:ease-in-out before:duration-300 after:ease-in-out after:duration-300 before:content-['['] after:content-[']']"
          tabindex="-1"
        >
          Submit
        </button>
      </div>
    </form>
  </div>
  <div
    class="col-span-4 flex gap-4 flex-wrap text-xs sm:col-start-5 sm:gap-8 uppercase"
  >
    <a
      href="/"
      class="text-gray-400 hover:text-gray-900 ease-in-out duration-300"
      >Legal Notice</a
    ><a
      href="/"
      class="text-gray-400 hover:text-gray-900 ease-in-out duration-300"
      >Privacy Policy</a
    >
    <a
      href="/"
      class="text-gray-400 hover:text-gray-900 ease-in-out duration-300"
      target="_blank"
      rel="noreferer"
      data-svelte-h="svelte-otdb53">Website by No Plans</a
    >
  </div>
</footer>
