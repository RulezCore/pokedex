<template>
  <b-container>
    <div class="header my-4">
      <h1>Categorias</h1>
      <hr />

      <div class="input-group mb-3">
        <input
          type="text"
          class="form-control"
          placeholder="Buscar por tipo"
          aria-label="Recipient's username"
          aria-describedby="basic-addon2"
          v-model="searchText"
          @keydown="fadeCard"
        />
        <div class="input-group-append">
          <button class="btn btn-primary" type="button">
            <font-awesome-icon icon="search" />
          </button>
        </div>
      </div>
    </div>
    <div class="row tarjetas">
      <!-- Bucle cards -->
      <div class="col-md-4" v-for="(type, index) in filtredList" :key="type.name">
        <div class>
          <b-card
            :title="type.name"
            :img-src="listImgCard[index]"
            img-alt="Image"
            img-top
            tag="article"
            style="max-width: 20rem;"
            class="mb-2"
          >
          
            <b-card-text></b-card-text>

            <a class="btn btn-primary" :href="'/categorias/' + extractId(type.url)">
              Mas informacion
              <font-awesome-icon icon="arrow-circle-right" />
            </a>
          </b-card>
          
        </div>
      </div>
    </div>
  </b-container>
</template>

<script>
export default {
  data() {
    return {
      searchText: "",
      listImgCard: ['https://i.ytimg.com/vi/q_Fmh32SLks/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/uiv5GEd0Zzc/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/inE_NHjK3fE/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/NU_Z-qkSCYs/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/D2QyVZiJEt4/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/h55zVd7id1s/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/_4aAO8wHCRc/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/9THsZhlJU6k/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/9TPkR1MmB5M/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/NW0rNI1sYQM/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/bzS5hE028z0/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/rRmcJ7PgTQ0/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/cPyNhxB_3cM/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/CyFxRZoJAZU/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/EheZsIMZnKo/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/0dwjy-0uFVI/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/pa-dNXU0oF0/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/ChAkfAMVOzs/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/ChAkfAMVOzs/maxresdefault.jpg',
                    'https://i.ytimg.com/vi/ChAkfAMVOzs/maxresdefault.jpg'
                    ],
      imgCard: ''
    };
  },

  asyncData({ $axios }) {
    return $axios.get("/type").then(res => {
      return {
        types: res.data.results
      };
    });
  },

  components: {},

  methods: {
    fadeCard(e) {
      console.log(e);
      document.querySelector(".tarjetas").style.opacity = 0;
      if (e) {
        setTimeout(function() {
          document.querySelector(".tarjetas").style.opacity = 1;
        }, 500);
        
      } else {
        document.querySelector(".tarjetas").style.opacity = 1;
      }
    },

    extractId(url) {
      var parts = url.split("/")
      return parts[6]
      
    }
  },

  computed: {
    filtredList() {
      var vm = this;
      return this.types.filter(function(type) {
        if (type.name.toLowerCase().includes(vm.searchText.toLowerCase())) {
          return true;
        } else {
          return false;
        }
      });
    }
  }
};
</script>

<style lang="scss">
.input-group {
  .btn-primary {
    background: #3589cc !important;
  }
}
.tarjetas {
  transition: .5s;
  .card {
  transition: 0.5s;
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
}
}
</style>