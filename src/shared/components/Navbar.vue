<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";
import { useRoute } from "vue-router";
import { Download, Menu, X } from "lucide-vue-next";
import gsap from "gsap";

const isScrolled = ref(false);
const isMobileMenuOpen = ref(false);
const route = useRoute();

const navLinks = [
  { name: "Home", path: "/" },
  { name: "Projects", path: "/projects" },
  { name: "About", path: "/about" },
  { name: "Contact", path: "/contact" },
];

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
  gsap.from(".nav-item", {
    y: -30,
    opacity: 0,
    duration: 1,
    stagger: 0.1,
    ease: "power4.out",
    delay: 0.3,
  });
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<template>
  <nav
    class="fixed top-0 inset-x-0 z-100 transition-all duration-700"
    :class="
      isScrolled
        ? 'py-4 bg-white/70 backdrop-blur-3xl border-b border-blue-900/5 shadow-sm'
        : 'py-8'
    "
  >
    <div class="container-wide flex items-center justify-between">
      <!-- Logo -->
      <router-link to="/" class="nav-item flex items-center gap-3 group">
        <div
          class="w-10 h-10 rounded-xl bg-accent flex items-center justify-center font-black text-sm text-white group-hover:bg-neon group-hover:text-black transition-all duration-500 tracking-tighter"
        >
          RJ
        </div>
        <span class="font-display font-black text-xl tracking-tight"
          >ROHAN<span class="text-accent">.</span></span
        >
      </router-link>

      <!-- Desktop Links -->
      <div class="hidden md:flex items-center gap-10">
        <router-link
          v-for="link in navLinks"
          :key="link.name"
          :to="link.path"
          class="nav-item text-sm font-bold uppercase tracking-widest relative group transition-colors duration-300"
          :class="
            route.path === link.path
              ? 'text-[#1E3A8A]'
              : 'text-muted hover:text-[#1E3A8A]'
          "
        >
          {{ link.name }}
          <span
            class="absolute -bottom-1.5 left-0 h-0.5 bg-accent transition-all duration-500"
            :class="
              route.path === link.path ? 'w-full' : 'w-0 group-hover:w-full'
            "
          ></span>
        </router-link>
      </div>

      <!-- CTA Section -->
      <div class="nav-item flex items-center gap-4 lg:gap-8">
        <!-- Resume Link -->
        <a
          href="/Frontend_Resume.pdf"
          download="Rohan_Jadav_Resume.pdf"
          class="hidden md:flex items-center gap-2 px-4 py-2 rounded-full bg-accent text-white text-xs font-black uppercase tracking-[0.15em] hover:bg-neon hover:shadow-lg hover:shadow-neon/30 transition-all duration-300"
        >
          <Download :size="14" />
          Resume
        </a>

        <!-- Hire Me -->
        <router-link
          to="/contact"
          class="hidden md:flex px-7 py-3 rounded-full border border-blue-900/10 text-xs font-bold uppercase tracking-widest hover:bg-[#1E3A8A] hover:text-white transition-all duration-500 backdrop-blur-sm shadow-sm"
        >
          Hire Me
        </router-link>

        <!-- Mobile Hamburger -->
        <button
          class="md:hidden w-10 h-10 flex items-center justify-center relative z-50 text-[#1E3A8A]"
          @click="isMobileMenuOpen = !isMobileMenuOpen"
        >
          <Menu v-if="!isMobileMenuOpen" :size="24" />
          <X v-else :size="24" />
        </button>
      </div>
    </div>

    <!-- Mobile Menu -->
    <Transition name="mobile-menu">
      <div
        v-if="isMobileMenuOpen"
        class="md:hidden absolute top-full inset-x-0 bg-white/95 backdrop-blur-3xl border-b border-black/5 px-6 py-8 flex flex-col gap-6"
      >
        <router-link
          v-for="link in navLinks"
          :key="link.name"
          :to="link.path"
          class="text-2xl font-black uppercase tracking-tight hover:text-accent transition-colors duration-300"
          :class="route.path === link.path ? 'text-accent' : 'text-[#1E3A8A]'"
          @click="isMobileMenuOpen = false"
        >
          {{ link.name }}
        </router-link>
        
        <!-- Mobile Resume Button -->
        <a
          href="/Frontend_Resume.pdf"
          download="Rohan_Jadav_Resume.pdf"
          class="flex items-center justify-center gap-2 px-6 py-4 rounded-full bg-accent text-white text-base font-black uppercase tracking-wider hover:bg-neon hover:shadow-lg hover:shadow-neon/30 transition-all duration-300"
          @click="isMobileMenuOpen = false"
        >
          <Download :size="20" />
          Download Resume
        </a>
      </div>
    </Transition>
  </nav>
</template>

<style scoped>
.mobile-menu-enter-active,
.mobile-menu-leave-active {
  transition:
    opacity 0.3s ease,
    transform 0.3s ease;
}
.mobile-menu-enter-from,
.mobile-menu-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
