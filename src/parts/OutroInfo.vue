<script setup>
import { ref } from 'vue'

const copied = ref(false)

const copyLink = async () => {
  try {
    const url = window.location.origin + window.location.pathname

    await navigator.clipboard.writeText(url)

    copied.value = true

    setTimeout(() => {
      copied.value = false
    }, 1000)
  } catch (e) {
    console.error('Erreur copie', e)
  }
}
</script>

<template>
  <div class="screen">
    <div class="row">
      <div class="col-12 col-sm-10 col-lg-5 offset-0 offset-lg-1">
        <p>
          Vous êtes <strong>victime</strong> ou avez été
          <strong>victime de violences</strong> physiques, psychiques ou sexuelles ou avez besoin
          d’aide ?
          <a href="https://www.victimepasseule.ch/post/aide-aux-victimes">
            <strong>Voici la liste des contacts utiles.</strong>
          </a>
        </p>
        <p>
          <strong>Vous souhaitez témoigner anonymement ?</strong> Vous pouvez transmettre votre
          témoignage <a href="https://www.victimepasseule.ch/formulaire"><strong>ici</strong></a> !
        </p>
      </div>
      <div class="col-12 col-lg-4 offset-0 offset-lg-1">
        <div id="layout-responsive-button-emergency">
          <div id="layout-button-emergency">
            <div id="emergency">
              <p><strong>Numéros d'urgence</strong></p>
              <p>
                Police: <strong>117</strong><br />Ambulance: <strong>144</strong><br />La main
                tendue: <strong>143</strong><br /><a href="https://www.ciao.ch/">Ciao.ch</a
                ><br />Pro Juventute (pour les 11-20 ans): <strong>147</strong>
              </p>
            </div>
            <button @click="copyLink" :class="['btn-share', { 'btn-share--copied': copied }]">
              <strong>{{ copied ? 'Lien copié' : 'Partager le site' }}</strong>
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-md-7 col-lg-4 offset-md-1 offset-lg-2">
        <p>Par l'association <a href="https://www.victimepasseule.ch/">Victime pas seule</a></p>
        <p>
          Avec les partenaires <a href="https://www.zonta.ch/fr/">Zonta Club Fribourg</a> et
          <a href="https://swiss-soroptimist.ch/fr/">Soroptimist International Club Fribourg</a>
        </p>
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-sm-8 col-md-7 col-lg-5 offset-0 offset-sm-4 offset-md-5 offset-lg-7">
        <div id="credits">
          <div id="layout-credits-text">
            <p><strong>2026 © Victime pas seule</strong></p>
            <p>
              Réalisation
              <a href="https://www.eikon.ch/departments/eikonlab/"><strong>eikonlab</strong></a
              ><br />
              Conception du site - Oliva Baeriswyl et Flavio Rotunno<br />After movie - Laurianne
              Sauteur et Elise Mutrux
            </p>
          </div>
          <img src="./../../img-credits.png" alt="" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Liens */
a {
  color: var(--color-blue);
  transition: all 0.2s ease;
  text-decoration: underline 1.4px;
}

a:hover {
  opacity: 0.6;
}

/* Mise en page encadré numéros */
#emergency,
#emergency a {
  color: var(--color-orange);
}

#emergency {
  border: solid 1.4px var(--color-orange);
  border-radius: 29px;
  padding: 30px;
}

#layout-button-emergency {
  max-width: 320px;
}

/* Crédits */
#credits p,
#credits strong {
  font-size: 15px;
  line-height: 16px;
  position: relative;
  z-index: 2;
}

#credits strong {
  font-weight: 600;
}

#credits {
  position: relative;
}

#credits img {
  opacity: 50%;
  width: 122px;

  position: absolute;
  top: -50px;
  left: -4px;
  z-index: 1;
}

#layout-credits-text {
  margin-left: 30px;
}

/* Bouton */
.btn-share {
  border-radius: 29px;
  padding: 12px 32px 15px;
  width: 100%;
  margin-top: 24px;

  border: 1.4px solid #8fa9c8;
  background-color: var(--color-light-blue);
  color: var(--color-blue);

  transition:
    transform 0.4s ease,
    color 0.2s ease,
    border 0.2s ease;
}

button:hover {
  color: var(--color-orange);
  border: 1.4px solid var(--color-orange);
  transform: scale(1.04);
}

.btn-share--copied {
  color: var(--color-orange);
  border: 1.4px solid var(--color-orange);
  transform: scale(1.04);
}

/* Responsive */
@media (min-width: 576px) and (max-width: 992px) {
  #layout-responsive-button-emergency {
    display: flex;
    justify-content: flex-end;
  }
}

@media (max-width: 576px) {
  #layout-button-emergency {
    max-width: 100%;
  }
}
</style>
