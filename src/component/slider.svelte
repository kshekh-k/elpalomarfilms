<script lang="ts">
  import { register } from "swiper/element/bundle";
  register();

  const videos = [
    {
      videowebm: "/videos/197485-905015019_small.webm",
      title: "Squid — Cro-Magnon Man",
      descrip: "Rory Alexander Stewart",
    },
    {
      videowebm: "/videos/217490_medium.webm",
      title: "Rosalía — Motomami",
      descrip: "STILLZ",
    },
    {
      videowebm: "/videos/8771136-uhd_2160_4096_25fps.webm",
      title: "Axe — Long Lasting",
      descrip: "Andreas Nilsson",
    },

    {
      videowebm: "/videos/13050886_1080_1920_30fps.webm",
      title: "Expedia — Nothing (DC)",
      descrip: "Lope Serrano",
    },
    {
      videowebm: "/videos/13343149_1080_1920_30fps.webm",
      title: "Travis Scott — Sirens",
      descrip: " ",
    },
    {
      videowebm: "/videos/13383668_1080_1920_30fps.webm",
      title: "Telefónica — Neuron (DC)",
      descrip: "Nicolás Méndez",
    },
    {
      videowebm: "/videos/13392869_1080_1920_60fps.webm",
      title: "Saint Jhn — Body On Me",
      descrip: "Alex Gargot",
    },
    {
      videowebm: "/videos/13425380_2160_3840_25fps.webm",
      title: "The Chemical Brothers ft Beck — Skipping Like A Stone",
      descrip: "Pensacola",
    },
    {
      videowebm: "/videos/16636239-hd_1920_1080_50fps.webm",
      title: "La Causa del Accidente que Provocó el Incendio",
      descrip: "Lope Serrano",
    },
  ];
</script>

<swiper-container
  space-between={60}
  free-mode={true}
  momentum={true}
  allow-touchmove={false}
  autoplay-delay={0}
  loop={true}
  speed={15000}
  slides-per-view="auto"
>
  {#each videos as item, i (i)}
    <swiper-slide class="w-auto">
      <div style="border-radius: 25px; height: 75vh;" class="overflow-hidden">
        <video
          class="w-full h-full object-cover"
          autoplay
          loop
          muted
          playsinline
        >
          <source src={item.videowebm} type="video/mp4" />
        </video>
      </div>
      <div
        class="flex flex-col gap-1 p-2 uppercase text-center text-gray-900 text-xl"
      >
        <h3 class="">{item.title}</h3>
        <p class="">{item.descrip}</p>
      </div>
    </swiper-slide>
  {/each}
</swiper-container>

<!-- <div
  class="flex justify-center items-stretch gap-2 active:cursor-grabbing flex-1 flex-col 2xl:p-5 bg-red-600"
>
  <div
    class="flex items-center justify-center flex-1 overflow-hidden rounded-lg shadow-lg bg-blue-600"
  ></div>
  <div class="flex flex-col gap-1 p-2 uppercase text-center text-gray-900">
    <h3 class="font-semibold">Hello World</h3>
    <p class="font-semibold">lorem ipsum doler</p>
  </div>
</div> -->

<!-- <div aria-controls="scroller" aria-hidden="true" class="block">
  {#if mounted}
    <swiper-container
      slides-per-view={1}
      space-between={spaceBetween}
      loop={true}
      centeredSlides={true}
      autoplay={false}
      pagination={false}
      breakpoints={{
        768: {
          slidesPerView: 2,
          spaceBetween: 10,
        },
        1024: {
          slidesPerView: 3,
          spaceBetween: 10,
        },
      }}
      on:swiperprogress={onProgress}
      on:swiperslidechange={onSlideChange}
    >
      {#each videos as item, i (i)}
        <swiper-slide>
          <div
            class="flex justify-center items-stretch gap-2 active:cursor-grabbing flex-1 w-full 2xl:w-[calc(100vw-20rem)] max-w-full h-140 flex-col 2xl:p-5"
          >
            <div
              class="flex items-center justify-center flex-1 overflow-hidden rounded-lg shadow-lg"
            >
              <video
                class="w-full h-full object-cover"
                autoplay
                loop
                muted
                playsinline
              >
                <source src={item.videowebm} type="video/mp4" />
              </video>
            </div>
            <div
              class="flex flex-col gap-1 p-2 uppercase text-center text-gray-900"
            >
              <h3 class="font-semibold">{item.title}</h3>
              <p class="font-semibold">{item.descrip}</p>
            </div>
          </div>
        </swiper-slide>
      {/each}
    </swiper-container>
  {/if}
</div> -->
