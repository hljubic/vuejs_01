<template>
  <div id="app">
    <naslovnica naslov="Dohvat podataka!" podnaslov="Koristimo Axios!"/>

    <b-container>
      <popis-nastavnika />
    </b-container> 
  </div>
</template>

<script>
import Naslovnica from './components/Naslovnica'
import PopisNastavnika from './components/PopisNastavnika'

export default {
  name: 'App',
  components: {
    Naslovnica,
    PopisNastavnika
  }
}
</script>