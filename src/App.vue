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
  // mm.add('(max-width: 992px)', () => {
  //   const timeline = document.querySelector('#timeline-container-mobile')
  //   const section = document.querySelector('#main')

  //   if (!timeline || !section) return

  //   const getScrollDistance = () => {
  //     return timeline.scrollWidth - window.innerWidth
  //   }

  //   const getSectionScroll = () => {
  //     return section.offsetHeight - window.innerHeight
  //   }

  //   if (getScrollDistance() <= 0) return

  //   ScrollTrigger.create({
  //     trigger: section,
  //     start: 'top top',
  //     end: 'bottom bottom',
  //     onEnter: () => {
  //       gsap.to(timeline, { y: 0, opacity: 1, duration: 0.5 })
  //     },
  //     onLeave: () => {
  //       gsap.to(timeline, { y: 50, opacity: 0, duration: 0.5 })
  //     },
  //     onEnterBack: () => {
  //       gsap.to(timeline, { y: 0, opacity: 1, duration: 0.5 })
  //     },
  //     onLeaveBack: () => {
  //       gsap.to(timeline, { y: 50, opacity: 0, duration: 0.5 })
  //     },
  //   })

  //   gsap.to(timeline, {
  //     x: () => -getScrollDistance(),
  //     ease: 'none',
  //     scrollTrigger: {
  //       trigger: section,
  //       start: 'top top',
  //       end: () => `+=${getSectionScroll()}`,
  //       scrub: true,
  //       invalidateOnRefresh: true,
  //     },
  //   })
  // })
  mm.add('(max-width: 992px)', () => {
    const timeline = document.querySelector('#timeline-content-mobile')
    const section = document.querySelector('#main')

    if (!timeline || !section) return

    const getMoveX = () => {
      return timeline.scrollWidth - window.innerWidth
    }

    const getScroll = () => {
      return section.offsetHeight - window.innerHeight
    }

    if (getMoveX() <= 0) return

    gsap.to(timeline, {
      x: () => -getMoveX(),
      ease: 'none',
      scrollTrigger: {
        trigger: section,
        start: 'top top',
        end: () => `+=${getScroll()}`,
        scrub: true,
        invalidateOnRefresh: true,
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
        <div id="timeline-content-mobile">
          <TimelineMobile></TimelineMobile>
        </div>
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
/* #timeline-container-mobile {
  position: fixed;
  bottom: 0;
  left: 0;
  z-index: 10;
  pointer-events: none;

  display: none;
  opacity: 0;
  overflow: hidden;
}

#timeline-content-mobile {
  width: max-content;
} */

/* Frise mobile v2 */
#timeline-container-mobile {
  position: sticky;
  bottom: 0;
  left: 0;
  z-index: 20;
  pointer-events: none;

  width: 100%;
  height: auto;

  display: none;
  opacity: 0;
  overflow: hidden;
}

#timeline-content-mobile {
  width: max-content;
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

  background: var(--color-white);

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
    flex-direction: column-reverse;
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
