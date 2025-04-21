<script lang="ts">
  import { register } from "swiper/element/bundle";
  import "vidstack/bundle";
  import { collection, getDocs, getFirestore, query } from "firebase/firestore";
  import { onMount } from "svelte";
  import { firebaseApp } from "$lib/firebase";
  register();

  type Video = { vimeoId: string; title: string; description: string };
  let loading = true;
  let videos: Video[] = [];

  onMount(async () => {
    loading = true;
    const db = getFirestore(firebaseApp);
    const q = query(collection(db, "films"));

    const querySnapshot = await getDocs(q);
    // @ts-ignore
    videos = querySnapshot.docs.map((doc) => ({
      id: doc.id,
      ...doc.data(),
    }));
    console.log(videos);
    loading = false;
  });
</script>

<div>
  {#if loading}
    <div style="height: 75vh"></div>
  {:else}
    <swiper-container
      space-between={60}
      free-mode={true}
      momentum={true}
      slides-per-view="auto"
      autoplay-delay={0}
      speed={15000}
    >
      {#each videos as item, i (i)}
        <swiper-slide class="w-auto">
          <div
            class="overflow-hidden"
            style="border-radius: 25px; height: 75svh;"
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
        </swiper-slide>
      {/each}
    </swiper-container>
  {/if}
</div>
