<script setup></script>

<template>
  <div class="screen">
    <h3>Messages les plus récurrents</h3>
    <div class="row">
      <div class="col-12">
        <div id="layout-sentence-top">
          <div>
            <p class="small-text">Tu n'es</p>
            <p class="big-text">pas seule</p>
          </div>
        </div>
      </div>
      <div class="col-9">
        <div id="layout-sentences">
          <div id="sentence-report">
            <p class="small-text">N'aie</p>
            <p class="big-text">pas peur</p>
            <p class="small-text" id="specific-margin-text-top-bottom">de</p>
            <p class="big-text">dénoncer</p>
          </div>
          <div id="sentence-violence">
            <p class="small-text">La</p>
            <p class="big-text">violence</p>
            <p class="small-text" id="specific-margin-text-bottom">n'est</p>
            <p class="big-text">jamais acceptable</p>
          </div>
          <div id="sentence-believe">
            <p class="small-text">Je te</p>
            <p class="big-text">crois</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Fonts */
.small-text {
  font-family: arima, sans-serif;
  font-size: 20px;
  font-weight: 300;
  line-height: 20px;
  margin: 0;
}

.big-text {
  font-family: arima, sans-serif;
  font-size: 38px;
  font-style: normal;
  font-weight: 600;
  margin-top: 5px;
  margin-bottom: 7px;
}

#specific-margin-text-bottom {
  margin-bottom: 10px;
}

#specific-margin-text-top-bottom {
  margin: 16px 0 10px;
  padding-left: 90px;
}

/* Mise en page */
#layout-sentence-top {
  display: flex;
  justify-content: center;
}

#layout-sentences {
  display: flex;
  justify-content: space-between;
}

/* Postion des mots */
#layout-sentence-top .small-text {
  padding-left: 20px;
}

#sentence-believe .big-text {
  padding-left: 20px;
}
</style>
