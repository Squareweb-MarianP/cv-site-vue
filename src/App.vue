<script setup>
import { ref, onMounted } from 'vue'
import Lenis from 'lenis'
import pozaProfil from './assets/images/Poza CV.webp'

const menuItems = [
  { name: 'Home', id: 'home', icon: '🏠' },
  { name: 'About me', id: 'about', icon: '👤' },
  { name: 'Experience', id: 'resume', icon: '📄' },
  { name: 'Projects', id: 'portfolio', icon: '💼' },
  { name: 'Education', id: 'education', icon: '🎓' },
  { name: 'Skills', id: 'skills', icon: '🛠️' },
  { name: 'Contact', id: 'contact', icon: '📧' },
]

const activeSection = ref('home')

onMounted(() => {
  const lenis = new Lenis({
    duration: 3.5,
    easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
    smoothWheel: true
  })

  function raf(time) {
    lenis.raf(time)
    requestAnimationFrame(raf)
  }
  requestAnimationFrame(raf)
  window.lenis = lenis
})

const scrollToSection = (id) => {
  activeSection.value = id;
  const element = document.querySelector(`#${id}`);
  if (element && window.lenis) {
    window.lenis.scrollTo(element, {
      offset: 0,
      duration: 2
    })
  }
}
</script>

<template>
  <div class="flex min-h-screen bg-[#0f0f0f] text-white font-sans selection:bg-[#28e98c]/30 italic">
    
    <aside class="fixed left-0 top-0 h-screen w-[340px] p-5 flex flex-col z-50">
  <div class="bg-[#1a1a1a] border border-white/10 rounded-[2rem] p-6 flex flex-col items-center shadow-2xl h-full overflow-y-auto overflow-x-hidden custom-scrollbar">
    
    <div class="w-full aspect-[3/4] rounded-xl overflow-hidden mb-4 border border-white/5 bg-[#0f0f0f] shrink-0">
      <img 
        :src="pozaProfil" 
        alt="Marian Pătrașcu" 
        class="w-full h-full object-cover object-top" 
      />
    </div>

    <div class="text-center w-full shrink-0">
      <h1 class="text-2xl font-bold mb-2 tracking-tight not-italic">Marian Pătrașcu</h1>
      
      <div class="inline-flex items-center gap-2 px-3 py-1 bg-white/5 border border-white/10 rounded-full mb-5">
        <span class="w-2 h-2 bg-[#28e98c] rounded-full animate-pulse shadow-[0_0_8px_#28e98c]"></span>
        <span class="text-[9px] uppercase font-black tracking-widest text-slate-400 not-italic">Available for work</span>
      </div>

      <div class="w-full space-y-2 mb-6 text-[11px]">
        <button @click="scrollToSection('contact')" class="flex items-center justify-center w-full py-3 bg-[#28e98c] text-black font-bold rounded-xl hover:bg-[#28e98c]/90 transition-all uppercase tracking-widest not-italic">
          Contact Me
        </button>
        <div class="grid grid-cols-2 gap-2">
          <button class="flex items-center justify-center py-2.5 bg-[#222] border border-white/5 rounded-lg hover:border-[#28e98c]/50 transition-colors font-bold uppercase tracking-tighter not-italic">
            CV PDF
          </button>
          <a href="#" target="_blank" class="flex items-center justify-center py-2.5 bg-[#222] border border-white/5 rounded-lg hover:border-[#28e98c]/50 transition-colors font-bold uppercase tracking-tighter text-blue-400 not-italic">
            LinkedIn
          </a>
        </div>
      </div>
    </div>

    <nav class="w-full pt-4 border-t border-white/5">
      <ul class="space-y-0.5">
        <li v-for="item in menuItems" :key="item.id">
          <button 
            @click="scrollToSection(item.id)"
            class="w-full flex items-center justify-between px-3 py-2 rounded-lg transition-all duration-300 group"
            :class="activeSection === item.id ? 'text-[#28e98c] bg-white/5' : 'text-slate-500 hover:text-white'"
          >
            <div class="flex items-center gap-2.5">
              <span class="text-base">{{ item.icon }}</span>
              <span class="font-bold text-[10px] uppercase tracking-[0.15em] not-italic">{{ item.name }}</span>
            </div>
            <div 
              class="w-1 h-1 rounded-full bg-[#28e98c] transition-opacity"
              :class="activeSection === item.id ? 'opacity-100' : 'opacity-0'"
            ></div>
          </button>
        </li>
      </ul>
    </nav>
  </div>
</aside>
    <main class="ml-[380px] w-full px-12">
      
      <section id="home" class="min-h-screen flex flex-col justify-center py-20">
        <span class="text-[#28e98c] uppercase tracking-[0.3em] font-bold text-[10px] mb-6 border border-[#28e98c]/20 px-4 py-1 rounded-full w-fit not-italic">
          👋 Intro
        </span>
        <h2 class="text-[5rem] font-bold leading-[1.1] tracking-tighter mb-8 italic">
          I'm <span class="text-[#28e98c]">Marian</span>,<br /> 
          a Junior Web Developer <br /> 
          Building for Tomorrow.
        </h2>
        <p class="text-xl text-slate-400 max-w-2xl leading-relaxed">
          Pasionat de Vue.js și design modern. Îmi place să creez interfețe care nu doar funcționează, ci spun o poveste.
        </p>
      </section>

      <section id="about" class="min-h-screen py-20 border-t border-white/5">
        <h2 class="text-5xl font-bold mb-12 uppercase"><span class="text-[#28e98c]">01.</span> About Me</h2>
        <div class="grid grid-cols-2 gap-12 text-slate-400 leading-relaxed text-lg">
          <p>
            Drumul meu în programare a început din curiozitatea de a înțelege cum funcționează internetul sub capotă. Astăzi, mă concentrez pe tehnologii precum Vue 3 și Tailwind CSS pentru a construi experiențe digitale rapide.
          </p>
          <div class="bg-[#1a1a1a] p-8 rounded-3xl border border-white/5 shadow-xl not-italic">
             <h4 class="text-white font-bold mb-4 uppercase tracking-widest text-sm">Tech Focus</h4>
             <ul class="space-y-2 text-[#28e98c] font-mono text-sm">
                <li>▹ Vue 3 (Composition API)</li>
                <li>▹ Tailwind CSS v4</li>
                <li>▹ JavaScript ES6+</li>
                <li>▹ Node.js (Learning)</li>
             </ul>
          </div>
        </div>
      </section>

      <section id="resume" class="min-h-screen py-20 border-t border-white/5">
        <h2 class="text-5xl font-bold uppercase"><span class="text-[#28e98c]">02.</span> Experience</h2>
      </section>
      
      <section id="portfolio" class="min-h-screen py-20 border-t border-white/5">
        <h2 class="text-5xl font-bold uppercase"><span class="text-[#28e98c]">03.</span> Projects</h2>
      </section>

      <section id="education" class="min-h-screen py-20 border-t border-white/5 text-slate-700 uppercase">Education</section>
      <section id="skills" class="min-h-screen py-20 border-t border-white/5 text-slate-700 uppercase">Skills</section>
      <section id="testimonials" class="min-h-screen py-20 border-t border-white/5 text-slate-700 uppercase">Testimonials</section>

      <section id="contact" class="min-h-screen py-20 border-t border-white/5">
        <h2 class="text-5xl font-bold mb-16 uppercase"><span class="text-[#28e98c]">07.</span> Contact</h2>
        
        <div class="grid grid-cols-2 gap-20">
          <div class="space-y-8">
            <h3 class="text-3xl font-bold italic">Let's work together!</h3>
            <p class="text-slate-400 leading-relaxed">Ești interesat de o colaborare sau vrei doar să spui salut? Trimite-mi un mesaj!</p>
            
            <div class="space-y-6">
              <div class="flex flex-col">
                <span class="text-[10px] uppercase text-slate-500 tracking-widest mb-1 not-italic font-black">Email</span>
                <span class="text-xl font-bold">patrascu.m@hotmail.com</span>
              </div>
              <div class="flex flex-col">
                <span class="text-[10px] uppercase text-slate-500 tracking-widest mb-1 not-italic font-black">Locație</span>
                <span class="text-xl font-bold">România, București</span>
              </div>
            </div>
          </div>

          <div class="bg-[#1a1a1a] p-10 rounded-[2.5rem] border border-white/5 not-italic">
            <form class="space-y-6">
              <div class="grid grid-cols-2 gap-4 text-[10px] font-black uppercase tracking-widest">
                <div class="flex flex-col gap-2 text-slate-400">
                  <label class="ml-2">Nume</label>
                  <input type="text" class="bg-white/5 border border-white/10 p-4 rounded-xl focus:border-[#28e98c] outline-none transition-colors text-white" placeholder="John Doe" />
                </div>
                <div class="flex flex-col gap-2 text-slate-400">
                  <label class="ml-2">Email</label>
                  <input type="email" class="bg-white/5 border border-white/10 p-4 rounded-xl focus:border-[#28e98c] outline-none transition-colors text-white" placeholder="john@example.com" />
                </div>
              </div>
              <div class="flex flex-col gap-2 text-[10px] font-black uppercase tracking-widest text-slate-400">
                <label class="ml-2">Mesaj</label>
                <textarea rows="4" class="bg-white/5 border border-white/10 p-4 rounded-xl focus:border-[#28e98c] outline-none transition-colors text-white" placeholder="Salut, aș vrea să..."></textarea>
              </div>
              <button class="w-full py-5 bg-[#28e98c] text-black font-black uppercase tracking-widest rounded-xl hover:scale-[1.02] transition-transform">
                Send Message
              </button>
            </form>
          </div>
        </div>
      </section>

    </main>
  </div>
</template>

<style>
/* Stiluri pentru Lenis */
html.lenis {
  height: auto;
}
.lenis.lenis-smooth {
  scroll-behavior: auto !important;
}
.lenis.lenis-smooth [data-lenis-prevent] {
  overscroll-behavior: contain;
}
.lenis.lenis-stopped {
  overflow: hidden;
}

/* Scrollbar personalizat pentru sidebar daca e nevoie */
.custom-scrollbar::-webkit-scrollbar {
  width: 4px;
}
.custom-scrollbar::-webkit-scrollbar-track {
  background: transparent;
}
.custom-scrollbar::-webkit-scrollbar-thumb {
  background: #28e98c22;
  border-radius: 10px;
}
</style>