<script setup>
import ButtonShare from '../components/ButtonShare.vue'
</script>

<template>
  <div>
    <div>
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
        témoignage
        <a href="https://www.victimepasseule.ch/formulaire"><strong>ici !</strong></a>
      </p>
    </div>
    <div>
      <p>Par l'association <a href="https://www.victimepasseule.ch/">Victime pas seule</a></p>
      <p>
        Avec les partenaires <a href="https://www.zonta.ch/fr/">Zonta Club Fribourg</a> et
        <a href="https://swiss-soroptimist.ch/fr/">Soroptimist International Club Fribourg</a>
      </p>
    </div>
  </div>
  <div>
    <div class="emergency">
      <p><strong>Numéros d'urgence</strong></p>
      <p>
        Police: <strong>117</strong><br />Ambulance: <strong>144</strong><br />La main tendue:
        <strong>143</strong><br /><a href="https://www.ciao.ch/">Ciao.ch</a><br />Pro Juventute
        (pour les 11-20 ans): <strong>147</strong>
      </p>
    </div>
    <ButtonShare></ButtonShare>
  </div>
  <div class="credits">
    <img src="./../../img-credits.png" alt="" />
    <p>2026 © Victime pas seule</p>
    <p>
      Réalisation <a href="https://www.eikon.ch/departments/eikonlab/"><strong>eikonlab</strong></a
      ><br />
      Conception du site - Oliva Baeriswyl et Flavio Rotunno<br />After movie - Laurianne Sauteur et
      Elise Mutrux
    </p>
  </div>
</template>

<style scoped>
a {
  color: var(--color-blue);
}

.emergency,
.emergency a {
  color: var(--color-orange);
}

.credits p,
.credits strong {
  font-size: 15px;
  font-weight: 600;
  line-height: 16px;
}

.credits img {
  opacity: 50%;
}
</style>
