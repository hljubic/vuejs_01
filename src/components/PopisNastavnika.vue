<template>
  <div>
      <b-row>
          <b-col cols="4">
              <b-form-input v-model="pretraga" @keyup="dohvatiPodatke" placeholder="Ime nastavnika.. *"></b-form-input>
          </b-col>

          <b-col cols="2">
              <b-button @click="dohvatiPodatke">Dohvati podatke</b-button>
          </b-col>
      </b-row>

      <hr>

      <b-row>
          <b-col cols="3" v-for="nastavnik in nastavnici" v-bind:key="'nastavnik_' + nastavnik.o_id">
                <b-card
                    :title="nastavnik.o_ime + ' ' + nastavnik.o_prezime"
                    :img-src="'https://nastavnici.fpmoz.sum.ba/uploads/' + nastavnik.oo_profilna_slika"
                    img-height="240px"
                    img-top
                    tag="article"
                    style="max-width: 20rem;"
                    class="mb-2"
                >
                    <b-card-text>
                    {{ nastavnik.o_email }}
                    </b-card-text>

                    <b-button href="#" variant="primary">Pogledaj profil</b-button>
                </b-card>
          </b-col>
      </b-row>
  </div>
</template>

<script>
export default {
    name: 'PopisNastavnika',

    data: function() {
        return {
            pretraga: '',
            nastavnici: [] // Prazan niz
        }
    },

    methods: {
        dohvatiPodatke: function() {
            this.axios.get('https://nastavnici.fpmoz.sum.ba/index.php/profile/search/' + this.pretraga).then((response) => {
                console.log(response.data.osoblje)

                this.nastavnici = response.data.osoblje;

                for(let i=0; i < this.nastavnici.length; i++) {
                    if (this.nastavnici[i].oo_profilna_slika == null) {
                        this.nastavnici[i].oo_profilna_slika = 'logo_fpmoz.png'; // Postoji u istom direktoriju!
                    }
                }
            })
        }
    }
}
</script>

<style>

</style>