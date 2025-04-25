<script lang="ts">
  import { onMount } from "svelte";
  import { gsap } from "gsap";
  import { Draggable } from "gsap/Draggable";

  let slidesContainer: HTMLDivElement;
  let proxy: HTMLDivElement;

  onMount(() => {
    // Load InertiaPlugin via CDN
    const script = document.createElement("script");
    script.src =
      "https://cdn.jsdelivr.net/npm/inertia-plugin@0.6.0/dist/runtime.iife.min.js";
    script.onload = () => {
      if ((window as any).InertiaPlugin) {
        gsap.registerPlugin((window as any).InertiaPlugin);
        initSlider();
      } else {
        console.warn("InertiaPlugin not loaded");
      }
    };
    document.body.appendChild(script);
  });

  function initSlider() {
    const slides = slidesContainer.querySelectorAll(
      ".slide"
    ) as NodeListOf<HTMLElement>;
    const numSlides = slides.length;

    // Setup slide positions
    slides.forEach((slide, i) => {
      gsap.set(slide, { xPercent: i * 100 });
    });

    const wrap = wrapPartial(-100, (numSlides - 1) * 100);
    const timer = gsap.delayedCall(1.5, autoPlay);

    const animation = gsap.to(slides, {
      xPercent: `+=${numSlides * 100}`,
      ease: "none",
      duration: 100,
      repeat: -1,
      modifiers: {
        xPercent: wrap,
      },
    });

    proxy = document.createElement("div");
    document.body.appendChild(proxy);
    gsap.set(proxy, { x: 0 });

    const transform = (proxy as any)._gsTransform;
    let slideAnimation = gsap.to({}, 0.5, {});
    let slideWidth = 0;
    let wrapWidth = 0;

    resize();
    window.addEventListener("resize", resize);

    new Draggable(proxy, {
      trigger: slidesContainer,
      throwProps: true,
      inertia: true,
      onDrag: () => updateProgress(),
      onThrowUpdate: () => updateProgress(),
    });

    slidesContainer.addEventListener("wheel", (event: WheelEvent) => {
      event.preventDefault();
      animateSlides(event.deltaY / 30);
    });

    function animateSlides(direction: number) {
      timer.restart(true);
      slideAnimation.kill();
      const x = transform.x + direction * slideWidth;
      slideAnimation = gsap.to(proxy, {
        duration: 1,
        x,
        onUpdate: updateProgress,
      });
    }

    function updateProgress() {
      animation.progress(transform.x / wrapWidth);
    }

    function resize() {
      const norm = transform.x / wrapWidth || 0;
      slideWidth = slides[0].offsetWidth;
      wrapWidth = slideWidth * numSlides;
      gsap.set(proxy, { x: norm * wrapWidth });
      animateSlides(0);
      slideAnimation.progress(1);
    }

    function autoPlay() {
      animateSlides(1);
    }

    function wrapPartial(min: number, max: number) {
      const r = max - min;
      return (value: number) => {
        const v = value - min;
        return ((r + (v % r)) % r) + min;
      };
    }
  }
</script>

<div bind:this={slidesContainer} class="slides-container">
  <div class="slide">Slide 1</div>
  <div class="slide">Slide 2</div>
  <div class="slide">Slide 3</div>
</div>

<!-- <style>
  .slides-container {
    @apply relative w-full overflow-hidden   flex;
  }

  .slide {
    @apply min-w-full h-full flex items-center justify-center bg-gray-200 text-xl font-bold;
  }
</style> -->
