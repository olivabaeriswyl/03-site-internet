<script setup></script>

<template>
  <div class="screen">
    <h3>Message mis en avant</h3>
    <div class="row">
      <div class="col-12">
        <div id="layout-message">
          <div id="quote-block">
            <p class="informations" id="date">Date</p>
            <p id="quote">Tu es forte et tu mérites d’être respectée tel que tu es ♡</p>
            <p class="informations" id="name">Name</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Style texte informations  */
.informations {
  font-family: arima, sans-serif;
  font-size: 23px;
  font-weight: 300;
  line-height: 23px;
}

/* Mise en page  */
#layout-message {
  display: flex;
  justify-content: center;
  align-items: center;
}

#quote-block {
  max-width: 637px;
}

#quote {
  margin: 0 0 20px;
}

/* Position informations  */
#date {
  text-align: left;
}

#name {
  text-align: right;
}

@media (max-width: 768px) {
  .informations {
    font-family: arima, sans-serif;
    font-size: 21px;
    font-weight: 300;
    line-height: 10px;
  }

  #quote {
    margin: 0 0 10px;
  }
}
</style>
