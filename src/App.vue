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

  // DESKTOP PREMIER TEST
  // mm.add('(min-width: 993px)', () => {
  //   const timeline = document.querySelector('#timeline-container')
  //   const section = document.querySelector('main')

  //   gsap.set(timeline, { x: 80, opacity: 0, y: 0 })

  //   gsap
  //     .timeline({
  //       scrollTrigger: {
  //         trigger: section,
  //         start: 'top top',
  //         end: 'bottom bottom',
  //         scrub: 1,
  //       },
  //     })
  //     .to(timeline, {
  //       x: 0,
  //       opacity: 1,
  //       ease: 'power2.out',
  //       duration: 0.2,
  //     })
  //     .to(timeline, {
  //       y: () => -(timeline.scrollHeight - window.innerHeight),
  //       ease: 'none',
  //       duration: 1,
  //     })
  //     .to(timeline, {
  //       x: 0,
  //       opacity: 1,
  //       ease: 'power2.in',
  //       duration: 0.2,
  //     })
  // })

  // DESKTOP DEUXIÈME TEST
  // mm.add('(min-width: 993px)', () => {
  //   const timeline = document.querySelector('#timeline-container')
  //   const section = document.querySelector('main')

  //   // // hauteur de scroll de la section
  //   // const getSectionScroll = () => section.scrollHeight - window.innerHeight

  //   // // hauteur de scroll de la frise
  //   // const getTimelineScroll = () => timeline.scrollHeight - window.innerHeight

  //   // // sécurité : si la frise est plus petite → pas d’animation
  //   // if (getTimelineScroll() <= 0) return

  //   gsap.to(timeline, {
  //     y: () => -(timeline.scrollHeight - window.innerHeight),
  //     ease: 'none',
  //     scrollTrigger: {
  //       trigger: section,
  //       start: 'top top',
  //       end: 'bottom bottom',
  //       scrub: true,
  //       invalidateOnRefresh: true,
  //     },
  //   })

  //   // optionnel : gérer l'opacité en dehors de <main>
  //   ScrollTrigger.create({
  //     trigger: section,
  //     start: 'top top+=10%',
  //     end: 'bottom bottom-=10%',
  //     onEnter: () => gsap.set(timeline, { opacity: 1 }),
  //     onLeave: () => gsap.set(timeline, { opacity: 0 }),
  //     onEnterBack: () => gsap.set(timeline, { opacity: 1 }),
  //     onLeaveBack: () => gsap.set(timeline, { opacity: 0 }),
  //   })
  // })

  mm.add('(min-width: 993px)', () => {
    const timeline = document.querySelector('#timeline-content')
    const section = document.querySelector('#main')
    const endMarker = document.querySelector('#timeline-end')

    if (!timeline || !section || !endMarker) return

    gsap.to(timeline, {
      y: () =>
        endMarker.getBoundingClientRect().top -
        section.getBoundingClientRect().top -
        (timeline.offsetHeight - section.offsetHeight),
      ease: 'none',
      scrollTrigger: {
        trigger: section,
        start: 'top top',
        end: () => `bottom ${window.innerHeight}`, // on arrête au bottom du viewport
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
      <div id="timeline-content">
        <Timeline></Timeline>
      </div>
    </div>

    <PartStats></PartStats>
  </main>

  <div id="timeline-end" style="height: 0; width: 0"></div>

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

/* FRISE PREMIER TEST */
/* #timeline-container {
  position: fixed;
  top: 0;
  right: 0;
  z-index: 10;
  pointer-events: none;
}

#timeline-container {
  height: auto;
} */

/* FRISE DEUXIEME TEST */
#timeline-container {
  position: fixed;
  top: 0;
  right: 0;
  width: 230px;
  z-index: 10;
  pointer-events: none;
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
