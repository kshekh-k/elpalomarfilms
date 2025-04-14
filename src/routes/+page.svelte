<script lang="ts">
  import Header from "../component/header.svelte";
  import Footer from "../component/footer.svelte";
  import Slider from "../component/slider.svelte";
</script>

<main class="py-2 px-3">
  <div class="min-h-screen">
    <Header />
    <div class="overflow-hidden w-full">
      <Slider />
    </div>
    <Footer />
  </div>
</main>
