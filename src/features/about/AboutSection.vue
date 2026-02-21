<script setup lang="ts">
import { onMounted, ref } from "vue";
import { Layers, Trophy, Coffee, Code2 } from "lucide-vue-next";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

const props = defineProps<{ id?: string }>();
const textRef = ref<HTMLElement | null>(null);
const statsRef = ref<HTMLElement | null>(null);

onMounted(() => {
  if (!textRef.value) return;

  // Split text into lines for reveal
  const lines = textRef.value.querySelectorAll(".reveal-line");

  gsap.from(lines, {
    scrollTrigger: {
      trigger: textRef.value,
      start: "top 80%",
      toggleActions: "play none none none",
    },
    y: 100,
    opacity: 0,
    duration: 1.5,
    stagger: 0.2,
    ease: "expo.out",
  });

  // Stats Animation
  if (statsRef.value) {
    const stats = statsRef.value.querySelectorAll(".stat-item");
    gsap.from(stats, {
      scrollTrigger: {
        trigger: statsRef.value,
        start: "top 85%",
      },
      y: 50,
      opacity: 0,
      duration: 1.2,
      stagger: 0.1,
      ease: "power4.out",
    });
  }
});

const stats = [
  { label: "Experiences Built", value: "40+", icon: Layers },
  { label: "Design Awards", value: "12", icon: Trophy },
  { label: "Coffee Consumed", value: "∞", icon: Coffee },
  { label: "Lines of Code", value: "250k", icon: Code2 },
];
</script>

<template>
  <section :id="props.id" class="py-40 px-6 bg-background/30 backdrop-blur-sm">
    <div class="container-wide">
      <div class="mb-20">
        <h2
          class="text-xs uppercase tracking-[0.5em] font-bold text-accent mb-6"
        >
          Our DNA
        </h2>
      </div>

      <div ref="textRef" class="space-y-6">
        <p
          class="reveal-line text-5xl md:text-8xl font-black leading-[0.9]"
          style="letter-spacing: var(--tracking-hero)"
        >
          WE DON'T JUST <br />
          BUILD <span class="text-blue-900/10">WEBSITES;</span>
        </p>
        <p
          class="reveal-line text-5xl md:text-8xl font-black leading-[0.9] text-accent"
          style="letter-spacing: var(--tracking-hero)"
        >
          WE CRAFT DIGITAL <br />
          ECOSYSTEMS.
        </p>

        <div
          class="reveal-line pt-16 max-w-3xl text-xl md:text-2xl text-muted font-medium leading-relaxed"
        >
          Based at the intersection of high-end design and precision
          engineering, we specialize in
          <span class="text-[#1E3A8A]">cinematic WebGL experiences</span>, fluid
          motion systems, and scalable production-grade architectures.
          <br /><br />
          We believe every pixel should serve a purpose, and every line of code
          should push the boundaries of modern-day interaction.
        </div>
      </div>

      <!-- Stats Grid -->
      <div
        ref="statsRef"
        class="grid grid-cols-2 md:grid-cols-4 gap-12 mt-40 pt-20 border-t border-blue-900/10"
      >
        <div
          v-for="stat in stats"
          :key="stat.label"
          class="stat-item group cursor-none"
        >
          <component
            :is="stat.icon"
            class="text-accent mb-6 w-8 h-8 group-hover:scale-110 transition-transform duration-500"
          />
          <div
            class="text-5xl md:text-6xl font-black text-[#1E3A8A] group-hover:text-accent-red transition-colors duration-500 mb-4"
          >
            {{ stat.value }}
          </div>
          <div class="text-xs uppercase tracking-[0.3em] text-muted font-bold">
            {{ stat.label }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Custom overrides if needed */
</style>
