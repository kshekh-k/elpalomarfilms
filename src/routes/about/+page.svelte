<script lang="ts">
  import Footer from "../../component/footer.svelte";
  import Header from "../../component/header.svelte";
  const location = [
    {
      title: "Barcelona",
      menu: [
        {
          label: "Partner & Global HOP",
          value: "Alba Barneda",
        },
        {
          label: "Executive Producer",
          value: "Marta Argullós",
        },
        {
          label: "Executive Producer",
          value: "Víctor Mata",
        },
        {
          label: "Executive Producer",
          value: "Laura Serra Estorch",
        },
        {
          label: "Executive Producer / Photo EP",
          value: "Diana C Milesi",
        },
        {
          label: "Bidding Producer",
          value: "Julia Carrasco",
        },
        {
          label: "Producer",
          value: "Christy Alcaraz",
        },
        {
          label: "Music Video Producer",
          value: "Anna Bacardit",
        },
        {
          label: "Head of Photography",
          value: "Maria Vives",
        },
        {
          label: "Photo Agent & Producer",
          value: "Aurora Muñoz",
        },
        { label: "Film & TV", value: "Xavi Vara" },
        { label: "Film & TV", value: "Marta Cruañas" },
        { label: "Production Manager", value: "Itsasne Santos" },
        { label: "Production Coordinator", value: "Noe Montero" },
        { label: "Production Assistant", value: "Alejandra de la Mora" },
        { label: "Photo Production Assistant", value: "Sara Martinez" },
        { label: "Goods", value: "Alex Fillat" },

        { label: "Goods", value: "Alicia Camps" },
        { label: "PostProduction Artist", value: "Álvaro P Posadas" },
        {
          label: "Head of PostProduction",
          value: "Marina Martínez Campomanes",
        },
        { label: "PostProduction Coordinator", value: "Javier Botella" },
        { label: "PostProduction Artist", value: "Marta Castillo" },
        { label: "Head of Researchers", value: "Álvaro Gimeno" },
        { label: "Researcher Coordinator", value: "Angie Bolea" },
        { label: "Researcher", value: "Cristian López" },
        { label: "Researcher", value: "Jorge García" },
        { label: "CFO", value: "Roger Mora" },
        { label: "Controller", value: "Pasqualino Raffa" },
        { label: "Accountant", value: "Deborah Pons" },
        { label: "Accountant Assistant", value: "Dolors Martinez" },
        { label: "Labour", value: "Sara Martínez" },
        { label: "Labour Assistant", value: "Nerea Gili" },
        { label: "Office Manager", value: "Rosa Navarro" },
        { label: "Warehouse Manager", value: "Andrés Ordóñez" },
      ],
    },

    {
      title: "London",
      menu: [
        {
          label: "Managing Director / EP",
          value: "Marta Bobić",
        },
        {
          label: "Executive Producer",
          value: "Daisy Gautier",
        },
        {
          label: "Producer",
          value: "Davey Ahern",
        },
        {
          label: "Head of Music Videos and Content",
          value: "Callum Harrison",
        },
        {
          label: "Directors Rep",
          value: "Tanya Ramsurrun",
        },
        {
          label: "Office Manager",
          value: "Arnie Muthucumarasamy",
        },
        {
          label: "Production Assistant",
          value: "Matilda Silversved Miralles",
        },
        {
          label: "Finance Manager",
          value: "Egle Kavaliauskaite",
        },
        {
          label: "Head of Communications",
          value: "Pablo F Chocrón",
        },
        {
          label: "Communications Assistant",
          value: "Ella Penfold",
        },
      ],
    },
    {
      title: "Los Angeles",
      menu: [
        { label: "Managing Executive Producer", value: "Charlotte Woodhead" },
        { label: "Head of Production", value: "John Moran" },
        { label: "Executive Producer", value: "Ellie Bartlett" },
        { label: "Heads of Operation", value: "Ananda Grace" },
        { label: "Production Coordinator", value: "Kiva Corshen" },
      ],
    },
    {
      title: "Founders",
      menu: [
        { label: "Co-Founder & Creative Director", value: "Nicolás Méndez" },
        { label: "Co-Founder & Creative Director", value: "Lope Serrano" },
        { label: "Partner & Global HOP", value: "Alba Barneda" },
      ],
    },
  ];
</script>

<main class="py-2">
  <div class="min-h-screen">
    <Header />
    <div class="overflow-hidden w-full my-20">
      <div class="grid grid-cols-12 px-24 gap-y-32">
        <div
          class="col-span-4 text-lg uppercase sm:col-span-8 sm:col-start-5 space-y-5"
        >
          <p>
            CANADA is a creative production company founded in 2008 when a small
            collective of directors came together, united by the desire to
            connect with an audience via meaningful, well-crafted films.
          </p>
          <p>
            Since then, we have grown to become a family of international
            creatives and producers with offices in Barcelona, London and Los
            Angeles.
          </p>
          <p>
            Our shared love for our work, our belief in the power of
            collaboration, the magic of people, and the wonder of true artistry
            unite everything we do.
          </p>
          <p>
            With decades of experience creating award-winning work by our
            directors and photographers, we’re proud to develop and produce our
            projects with a global approach.
          </p>
        </div>

        <div class="flex flex-col col-span-full sm:col-start-2 sm:gap-14">
          {#each location as item}
            <div
              class=" gap-8 col-span-full grid grid-cols-4 sm:col-span-10 sm:col-start-2 sm:grid-cols-10"
            >
              <h4
                class="col-span-full text-lg uppercase sm:col-span-7 sm:col-start-4"
              >
                {item.title}
              </h4>
              <div
                class="col-span-full grid grid-cols-2 gap-5 text-sm text-gray-900 font-medium"
              >
                {#each item.menu as menu}
                  <div class="grid grid-cols-4 gap-4 sm:grid-cols-5">
                    <div
                      class="col-span-2 text-right uppercase sm:col-span-3 sm:whitespace-pre"
                    >
                      {menu.label}
                    </div>
                    <div class="col-span-2">{menu.value}</div>
                  </div>
                {/each}
              </div>
            </div>
          {/each}
        </div>
      </div>
    </div>
    <Footer />
  </div>
</main>
