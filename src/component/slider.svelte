<script lang="ts">
  import { register } from "swiper/element/bundle";
  import "vidstack/bundle";
  register();

  const videos = [
    {
      videoId: "19231868",
      title: "Squid — Cro-Magnon Man",
      descrip: "Rory Alexander Stewart",
    },
    {
      videoId: "76979871",
      title: "Rosalía — Motomami",
      descrip: "STILLZ",
    },
    {
      videoId: "1076692645",
      title: "Axe — Long Lasting",
      descrip: "Andreas Nilsson",
    },
  ];
</script>

<swiper-container
  space-between={60}
  free-mode={true}
  momentum={true}
  loop={true}
  slides-per-view="auto"
>
  {#each videos as item, i (i)}
    <swiper-slide class="w-auto">
      <div class="overflow-hidden" style="border-radius: 25px; height: 75vh;">
        <media-player
          autoplay
          loop
          muted
          title="Sprite Fight"
          src={`vimeo/${item.videoId}`}
          style="height: 100%"
        >
          <media-provider></media-provider>
        </media-player>
      </div>
      <div
        class="flex flex-col gap-1 p-2 uppercase text-center text-gray-900 text-xl"
      >
        <h3>{item.title}</h3>
        <p>{item.descrip}</p>
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
