<script lang="ts">
  import emblaCarouselSvelte from "embla-carousel-svelte";
  import Autoplay from "embla-carousel-autoplay";
  import "vidstack/bundle";
  import { collection, getDocs, getFirestore, query } from "firebase/firestore";
  import { onMount } from "svelte";
  import { firebaseApp } from "$lib/firebase";

  type Video = { vimeoId: string; title: string; description: string };
  let loading = true;
  let videos: Video[] = [];
  let options = { loop: true };
  let plugins = [Autoplay()];
  onMount(async () => {
    loading = true;
    const db = getFirestore(firebaseApp);
    const q = query(collection(db, "films"));

    const querySnapshot = await getDocs(q);
    // @ts-ignore
    videos = querySnapshot.docs.map(doc => ({
      id: doc.id,
      ...doc.data(),
    }));
    console.log(videos);
    loading = false;
  });
</script>

<div
  class="embla overflow-hidden"
  use:emblaCarouselSvelte={{ options, plugins }}
>
  <div class="embla__container flex gap-10">
    {#each videos as item, i (i)}
      <div class="embla__slide max-w-full">
        <div
          class="overflow-hidden rounded-xl h-[450px] md:h-[75svh] flex-auto"
        >
          <media-player
            autoplay
            loop
            muted
            title="Sprite Fight"
            src={`vimeo/${item.vimeoId}`}
            style="height: 100%"
          >
            <media-provider></media-provider>
          </media-player>
        </div>
        <div
          class="flex flex-col gap-1 p-2 uppercase text-center text-gray-900 text-xl"
        >
          <h3>{item.title}</h3>
          <p>{item.description}</p>
        </div>
      </div>
    {/each}
  </div>
</div>

<style>
  .embla {
    overflow: hidden;
  }
  .embla__container {
    display: flex;
  }
  .embla__slide {
    flex: 0 0 auto;
    min-width: 0;
  }
</style>
