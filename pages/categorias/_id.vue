<template>
  <div class="container">
    <div class="row mt-5">
      <div class="col-md-4" v-for="(poke, index) in pokemons">
        <div v-for="(x, index) in poke">
          <b-card
            v-if="x.name"
            :title="x.name"
            :img-src="'https://raw.githubusercontent.com/PokeAPI/pokeapi/master/data/v2/sprites/pokemon/' + spritePoke(x.url) + '.png'"
            img-alt="Image"
            img-top
            style="max-width: 20rem;"
            class="mb-5 cardPoke"
          >

          <b-button href="#" variant="primary">More Information <font-awesome-icon icon="arrow-circle-right" /> </b-button>
          </b-card>
          
        </div>
    </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params, error, $axios }) {
    return $axios.get(`/type/${params.id}`).then(function(res) {
      // for(var list in res.data.pokemon) {
      //    for(var lista in list) {
      //      var nombre = lista[0]
      //    }
      // }
      
      return {
        pokemons: res.data.pokemon
        
      }
    });
  },
  methods: {
    spritePoke (url) {
      var partes = url.split('/')
      console.log(partes)
      return partes[6]
    }
  }
};
</script>

<style lang="scss">
  .cardPoke {
    box-shadow: 0px 3px 6px rgba($color: #000000, $alpha: .2);

    .card-body {
      display: flex;
      justify-content: center;
      flex-direction: column;

      .card-title {
        text-transform: capitalize;
        text-align: center;
      }

      .btn-primary {
        background: #ff615c !important;
        border-color: #b32f2a;
    }
    }

    img {
      width: 120px !important;
      margin: 0 auto;
    }
  }
</style>