<script lang="ts">
  import Footer from "../../component/footer.svelte";

  import Header from "../../component/header.svelte";

  interface Contact {
    name: string;
    email: string;
    phone: string;
  }

  interface LocalPost {
    lp: string;
    add: Contact[];
  }

  interface Officer {
    post: string;
    name?: string;
    email?: string;
    localpost?: LocalPost[];
  }

  interface Address {
    locality: string;
    phone: string;
    email: string;
  }

  interface HQ {
    location: string;
    officers: Officer[];
    address?: Address[];
  }
  const hqs: HQ[] = [
    {
      location: "Barcelona (HQ)",
      officers: [
        {
          post: "Executive Producer",
          name: "Marta Argullós",
          email: "marta.argullos@canadacanada.com",
        },
        {
          post: "Executive Producer",
          name: "Víctor Mata",
          email: "victor@canadacanada.com",
        },
        {
          post: "Executive Producer",
          name: "Laura Serra Estorch",
          email: "laura@canadacanada.com",
        },
        {
          post: "Executive Producer",
          name: "Diana C Milesi",
          email: "diana@canadacanada.com",
        },
        {
          post: "Co-Founder & Creative Director",
          name: "Nicolás Méndez",
          email: "nicolas@canadacanada.com",
        },
        {
          post: "Co-Founder & Creative Director",
          name: "Lope Serrano",
          email: "lope@canadacanada.com",
        },
        {
          post: "Partner & Global HOP",
          name: "Alba Barneda",
          email: "alba@canadacanada.com",
        },
      ],
      address: [
        {
          locality: "Almogàvers 68-70, 8º Barcelona, Spain, 08018",
          phone: "+34 93 356 84 83",
          email: "info@canadacanada.com",
        },
      ],
    },
    {
      location: "London",
      officers: [
        {
          post: "Managing Director",
          name: "Marta Bobić",
          email: "marta.bobic@canadacanada.com",
        },
        {
          post: "Executive Producer",
          name: "Daisy Gautier",
          email: "daisy@canadacanada.com",
        },
        {
          post: "Directors Rep",
          name: "Tanya Ramsurrun",
          email: "tanya@canadacanada.com",
        },
      ],
      address: [
        {
          locality: "1, Waterside, 44-48 Wharf Rd London, N1 7UX",
          phone: "+44 203 371 7652",
          email: "london@canadacanada.com",
        },
      ],
    },
    {
      location: "Los Angeles",
      officers: [
        {
          post: "Managing Executive Producer",
          name: "Charlotte Woodhead",
          email: "charlotte@canadacanada.com",
        },
        {
          post: "Head of Production",
          name: "John Moran",
          email: "john@canadacanada.com",
        },
        {
          post: "Executive Producer",
          name: "Ellie Bartlett",
          email: "ellie@canadacanada.com",
        },
        {
          post: "WEST COAST REPS",
          localpost: [
            {
              lp: "Bueno",
              add: [
                {
                  name: "Bryan Shrednick",
                  email: "bryan@wearebueno.com",
                  phone: "(310) 980-4900",
                },
                {
                  name: "Millie Munro",
                  email: "millie@wearebueno.com",
                  phone: "(310) 795-5305",
                },
              ],
            },
          ],
        },
        {
          post: "MIDWEST REPS",
          localpost: [
            {
              lp: "Collective Management",
              add: [
                {
                  name: "Sean Sullivan",
                  email: "sean@collectivemanagement.tv",
                  phone: "(646) 361-0933",
                },
              ],
            },
          ],
        },
        {
          post: "EAST COAST REPS",
          localpost: [
            {
              lp: "Hunky Dory",
              add: [
                {
                  name: "Gisela Limberg",
                  email: "gisela@hunkydoryus.com",
                  phone: "(917) 607-0303",
                },
                {
                  name: "Nata Andresen",
                  email: "nata@hunkydoryus.com",
                  phone: "(917) 334-3051",
                },
                {
                  name: "Taylor Powers",
                  email: "taylor@hunkydoryus.com",
                  phone: "(216) 538-9649",
                },
              ],
            },
          ],
        },
      ],
      address: [
        {
          locality: "8440 Warner Dr, STE A2, Culver City, CA 90232",
          phone: "+1 (323) 433 9675",
          email: "losangeles@canadacanada.com",
        },
      ],
    },
    {
      location: "PHOTO",
      officers: [
        {
          post: "Photo Executive Producer",
          name: "Diana C Milesi",
          email: "diana@canadacanada.com",
        },
        {
          post: "Head of Photography",
          name: "Maria Vives",
          email: "maria@canadacanada.com",
        },
        {
          post: "Photo Agent & Producer",
          name: "Aurora Muñoz",
          email: "aurora@canadacanada.com",
        },
      ],
    },
    {
      location: "FILM & TV",
      officers: [
        {
          post: "Film & TV",
          name: "Xavi Vara",
          email: "xavi@canadacanada.com",
        },
        {
          post: "Film & TV",
          name: "Marta Cruañas",
          email: "marta.cruanas@canadacanada.com",
        },
      ],
    },
    {
      location: "MUSIC VIDEOS",
      officers: [
        {
          post: "Head of Music Videos and Content",
          name: "Callum Harrison",
          email: "callum@canadacanada.com",
        },
        {
          post: "Music Video Producer",
          name: "Anna Bacardit",
          email: "anna@canadacanada.com",
        },
      ],
    },
    {
      location: "Press",
      officers: [
        {
          post: "Head of Communications",
          name: "Pablo F Chocron",
          email: "pablo@canadacanada.com",
        },
        {
          post: "Communications Assistant",
          name: "Ella Penfold",
          email: "ella@canadacanada.com",
        },
      ],
    },
  ];

  // Store open state for each HQ using a simple map
  let openStates: Record<number, boolean> = {};
</script>

<main class="py-2">
  <div class="min-h-screen">
    <Header />
    <div class="overflow-hidden w-full my-20">
      <div class="grid grid-cols-12 px-24 gap-y-10">
        {#each hqs as item, index}
          <div
            class="relative col-span-full grid cursor-pointer grid-cols-4 items-center gap-x-6 sm:col-span-10 sm:col-start-2 sm:grid-cols-10 sm:gap-x-8"
          >
            <h3
              class="col-span-full select-none text-xl sm:col-span-3 sm:text-right uppercase"
            >
              {item.location}
            </h3>
            <button
              on:click={() => (openStates[index] = !openStates[index])}
              aria-hidden="true"
              class="max-sm:absolute max-sm:-left-30 max-sm:top-5 sm:col-span-7"
              ><svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 20 20"
                fill="none"
                class="w-5 ease-in-out duration-300 {openStates[index]
                  ? 'rotate-0'
                  : '-rotate-45'}"
                ><path
                  stroke="currentColor"
                  stroke-linecap="round"
                  stroke-width="1.5"
                  d="m1 1 18 18m0-18L1 19"
                ></path></svg
              ></button
            >
            {#if openStates[index]}
              <div class="col-span-full overflow-hidden">
                <div
                  class="grid grid-cols-4 gap-4 pt-20 max-sm:pb-16 sm:grid-cols-10 sm:pt-4"
                >
                  {#each item.officers as officer}
                    <div
                      class="col-span-full col-start-1 grid grid-cols-4 gap-x-15 gap-y-5 sm:col-span-5 sm:col-start-1 sm:grid-cols-5 sm:gap-8"
                    >
                      <div
                        class="col-span-full uppercase sm:col-span-3 sm:whitespace-pre sm:text-right"
                      >
                        {officer.post}
                      </div>

                      {#if officer.localpost}
                        <div
                          class="flex flx-col gap-5 col-span-3 max-sm:col-start-2 sm:col-span-2"
                        >
                          {#each officer.localpost as localpost}
                            <div class="flex flex-col gap-5">
                              <p>{localpost.lp}</p>
                              {#each localpost.add as add}
                                <div class="flex flex-col gap-1">
                                  <p>{add.name}</p>
                                  <a href="mailto:${add.email}">{add.email}</a>
                                  <p>{add.phone}</p>
                                </div>
                              {/each}
                            </div>
                          {/each}
                        </div>
                      {:else}
                        <div
                          class="col-span-3 max-sm:col-start-2 sm:col-span-2"
                        >
                          {officer.name}
                          {officer.email}
                        </div>
                      {/if}
                    </div>
                  {/each}
                  {#if item.address}
                    <div
                      class="col-span-full row-start-1 mb-20 sm:col-span-3 sm:col-start-8 sm:row-span-3 sm:row-start-1 max-w-60"
                    >
                      {#each item.address as address}
                        <p>{address.locality}</p>
                        <p>{address.phone}</p>
                        <p>{address.email}</p>
                      {/each}
                    </div>
                  {/if}
                </div>
              </div>
            {/if}
          </div>
        {/each}
      </div>
    </div>
    <Footer />
  </div>
</main>
