<script setup>
import PartOutro from './sections/SectionOutro.vue'
import PartIntro from './sections/SectionIntro.vue'
import PartStats from './sections/SectionStats.vue'
import BurgerMenu from './components/BurgerMenu.vue'

import Timeline from './components/Timeline.vue'
import TimelineMobile from './components/TimelineMobile.vue'

import { onMounted } from 'vue'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

// Frise
onMounted(() => {
  const mm = gsap.matchMedia()

  mm.add('(min-width: 993px)', () => {
    const timeline = document.querySelector('#timeline-content')

    if (!timeline) return

    const getMoveY = () => {
      const timelineHeight = timeline.scrollHeight
      const viewportHeight = window.innerHeight

      // 🔥 distance réelle à parcourir
      return Math.max(timelineHeight - viewportHeight, 0)
    }

    gsap.to(timeline, {
      y: () => -getMoveY(),
      ease: 'none',
      scrollTrigger: {
        trigger: '#main',
        start: 'top top',
        end: '+=300%', // 🔥 3x viewport = 300vh
        scrub: true,
        invalidateOnRefresh: true,
        markers: false,
      },
    })
  })

  // FRISE MOBILE
  mm.add('(max-width: 992px)', () => {
    const timeline = document.querySelector('#timeline-container-mobile')
    const section = document.querySelector('main')

    gsap.set(timeline, { y: 50, opacity: 0, x: 0 })

    ScrollTrigger.create({
      trigger: section,
      start: 'top bottom',
      end: 'bottom bottom',
      onEnter: () => {
        gsap.to(timeline, { y: 0, opacity: 1, duration: 0.5 })
      },
      onLeave: () => {
        gsap.to(timeline, { y: 50, opacity: 0, duration: 0.5 })
      },
      onEnterBack: () => {
        gsap.to(timeline, { y: 0, opacity: 1, duration: 0.5 })
      },
      onLeaveBack: () => {
        gsap.to(timeline, { y: 50, opacity: 0, duration: 0.5 })
      },
    })

    const children = Array.from(timeline.children)

    gsap.to(children, {
      x: () => -(timeline.scrollWidth - window.innerWidth),
      ease: 'none',
      stagger: 0.1,
      scrollTrigger: {
        trigger: section,
        start: 'top bottom',
        end: 'bottom top',
        scrub: true,
      },
    })
  })
})
</script>

<template>
  <BurgerMenu></BurgerMenu>

  <header>
    <PartIntro @start="unlockScroll"></PartIntro>
  </header>

  <main id="main">
    <div id="timeline-container-mobile">
      <TimelineMobile></TimelineMobile>
    </div>

    <div id="timeline-container-desktop">
      <div id="timeline-position">
        <Timeline></Timeline>
      </div>
    </div>

    <PartStats></PartStats>
  </main>

  <footer>
    <PartOutro></PartOutro>
  </footer>
</template>

<style scoped>
/* Frise */
#main {
  position: relative;
  width: 100%;

  display: flex;
  flex-direction: row-reverse;
}

/* FRISE MOBILE */
#timeline-container-mobile {
  position: fixed;
  bottom: 0;
  left: 0;
  z-index: 10;
  pointer-events: none;

  display: none;
  opacity: 0;
  overflow: hidden;
}

@media (max-width: 992px) {
  #timeline-container-mobile {
    display: block;
    opacity: 1;
  }

  #timeline-container {
    display: none;
    opacity: 0;
  }
}

/* Timeline v3 */
#timeline-container-desktop {
  background: red;
  width: 230px;
  height: 100vh;
  position: sticky;
  top: 0;
  z-index: 10;
  pointer-events: none;
  overflow: hidden;
}

#timeline-content {
  width: 100%;
  height: auto;
}
</style>
