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

// Frise
gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
  const mm = gsap.matchMedia()

  // Frise desktop
  mm.add('(min-width: 993px)', () => {
    const timeline = document.querySelector('#timeline-content')

    if (!timeline) return

    const getMoveY = () => {
      const timelineHeight = timeline.scrollHeight
      const viewportHeight = window.innerHeight

      return Math.max(timelineHeight - viewportHeight, 0)
    }

    gsap.to(timeline, {
      y: () => -getMoveY(),
      ease: 'none',
      scrollTrigger: {
        trigger: '#main',
        start: 'top top',
        end: '+=300%',
        scrub: true,
        invalidateOnRefresh: true,
        markers: false,
      },
    })
  })

  // Frise mobile
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
  <div id="website">
    <BurgerMenu></BurgerMenu>

    <header>
      <PartIntro></PartIntro>
    </header>

    <main id="main">
      <div id="timeline-container-mobile">
        <TimelineMobile></TimelineMobile>
      </div>

      <div id="timeline-container-desktop">
        <div id="timeline-content">
          <Timeline></Timeline>
        </div>
      </div>

      <div id="section-content">
        <PartStats></PartStats>
      </div>
    </main>

    <footer>
      <PartOutro></PartOutro>
    </footer>
  </div>
</template>

<style scoped>
/* #website {
  overflow: hidden;
} */

/* Contenu entier et position frise */
#main {
  position: relative;
  width: 100%;

  display: flex;
  flex-direction: row-reverse;
}

/* Frise mobile */
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

/* Frise desktop */
#timeline-container-desktop {
  width: 230px;
  height: 100vh;
  position: sticky;
  top: 0;
  z-index: 10;
  pointer-events: none;
  overflow: hidden;
  flex-shrink: 0;

  background: red;

  -webkit-mask-image: linear-gradient(to bottom, transparent 0%, black 15%, black 100%);
  mask-image: linear-gradient(to bottom, transparent 0%, black 15%, black 100%);
}

#timeline-content {
  width: 100%;
  height: auto;
}

#main #section-content {
  flex: 1;
  min-width: 0;
}

/* Responsive */
@media (max-width: 992px) {
  #main {
    display: block;
  }

  #timeline-container-mobile {
    display: block;
    opacity: 1;
  }

  #timeline-container-desktop {
    display: none;
    opacity: 0;
  }
}
</style>
