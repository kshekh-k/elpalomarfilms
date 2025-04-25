<script lang="ts">
  import About from "../component/about.svelte";
  import Contact from "../component/contact.svelte";
  import Gsap from "../component/gsap.svelte";
  import Header from "../component/header.svelte";
  import Slider from "../component/slider.svelte";
  import { writable } from "svelte/store";
  import { onMount } from "svelte";
  const scrollY = writable(0);
  let activeSection = "home";

  // Simple parallax effect without external libraries
  const handleScroll = () => {
    // Update active section
    const sections = ["home", "about", "contact"];
    for (const section of sections) {
      const el = document.getElementById(section);
      if (el) {
        const rect = el.getBoundingClientRect();
        if (rect.top <= 100 && rect.bottom >= 100) {
          activeSection = section;
          break;
        }
      }
    }

    // Basic parallax effect with proper type casting
    const parallaxElements =
      document.querySelectorAll<HTMLElement>(".parallax-bg");

    parallaxElements.forEach(element => {
      const speed = parseFloat(element.dataset.speed || "0.5");
      const yPos = -(window.pageYOffset * speed);
      element.style.transform = `translateY(${yPos}px)`;
    });
  };

  onMount(() => {
    window.addEventListener("scroll", handleScroll);
    return () => window.removeEventListener("scroll", handleScroll);
  });
</script>

<main class="py-2 px-3" id="home">
  <div class="min-h-screen pt-18">
    <Header />
    <section class="overflow-hidden w-full pt-10">
      <!-- <Gsap /> -->
      <Slider />
    </section>

    <section
      class="flex flex-col md:grid md:grid-cols-12 gap-8 2xl:px-24 py-10"
    >
      <div class="md:max-w-60 md:col-span-4 max-w-32">
        <img
          src="/images/Logo-El-Palomar-FIilms.svg"
          alt="El Palomar FIilms"
          class="w-full"
        />
      </div>
      <div class="col-span-full flex flex-col gap-8 md:grid md:col-span-8">
        <div class="max-w-3xl flex flex-col gap-4">
          <h2 class="text-xl font-semibold italic uppercase">About Us</h2>
          <p class="text-xl italic">
            El Palomar Films is a creative studio based in Andalusia, working
            with honesty, sensitivity, and a strong personal vision.
          </p>
          <p class="text-xl italic">
            We are not an agency. We are creators. We tell stories that connect
            with what’s real—with people, with emotions, and with the place we
            come from. We believe in the power of well-crafted story telling,
            with out artifice, with truth.
          </p>
          <p class="text-xl italic">
            From the South of Spain, we offer a new perspective on our culture:—
            far from cliché, close to emotion. We embrace modern concepts that
            never for get where we come from or where we stand. We are
            responsible for every step of our productions: from casting, script
            writing, and art direction, to original music. This allows us to
            deliver truly unique, tailor-madepieces, with a recognizable
            signature and a language of our own.
          </p>
        </div>
        <div class="max-w-xl flex flex-col gap-4">
          <h2 class="text-2xl font-semibold italic uppercase">Contact Us</h2>
          <p class="text-xl italic">
            Tel+34691551111<br />
            info@elpalomarfilms.com
          </p>
        </div>
      </div>
    </section>
    <section id="about" class="min-h-screen pt-18">
      <About />
    </section>
    <section id="contact" class="min-h-screen pt-18">
      <Contact />
    </section>
    <!-- <Footer /> -->
  </div>
</main>
