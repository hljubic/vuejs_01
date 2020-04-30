<template>
  <div>
    <div>
      <b-jumbotron :header="naslov" :lead="podnaslov">
        <b-button variant="primary" href="#">Detalji</b-button>
      </b-jumbotron>
    </div>
  </div>
</template>

<script>
export default {
  name: "Naslovnica",
  props: ['naslov', 'podnaslov']
};
</script>
