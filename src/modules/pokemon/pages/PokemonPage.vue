<template>
  <h1 v-if="!pokemonCorrecto">Espere por favor...</h1>
  <div v-else>
    

      <h1>Juego Pokemon</h1>
      <label for="">Puntacion: {{ puntaje }} Intentos:{{ intentos }}</label>
      <PokemonImg
        :pokemonId="pokemonCorrecto.id"
        :muestraPokemon="showPokemon"
      />
      <PokemonOps
        :opciones="arreglo"
        v-on:seleccionado="revisarSeleccion($event)"
      />
  </div>

  <div v-if="puntaje != 0" class="gana">
    <h1>Has ganado</h1>
    <h2>Tu puntuacion es {{ puntaje }}</h2>
    <button @click="reiniciar()">REINICIAR</button>
  </div>
  <div v-if="puntaje == 0 && intentos == 0" class="pierde">
    <h1>Has Perdido</h1>
    <h2>Intentalo de nuevo</h2>
    <button @click="reiniciar()">REINICIAR</button>
  </div>
</template>
  
  <script>
import PokemonImg from "../components/PokemonImg.vue";
import PokemonOps from "../components/PokemonOps.vue";
import obtenerFachadaPokemon from "../helpers/clientePokemonAPI";
export default {
  data() {
    return {
      arreglo: [],
      pokemonCorrecto: null,
      showPokemon: false,
      intentos: 3,
      puntaje: 0,
    };
  },
  components: {
    PokemonImg,
    PokemonOps,
  },
  methods: {
    async cargaJuegoInicial() {
      const arregloPokemons = await obtenerFachadaPokemon();
      console.log(arregloPokemons);
      this.arreglo = arregloPokemons;
      const indicePokemon = Math.floor(Math.random() * 4);
      this.pokemonCorrecto = this.arreglo[indicePokemon];
      this.showPokemon = false;
    },
    revisarSeleccion(idSeleccionado) {
      console.log("evento en el padre");
      if (this.pokemonCorrecto.id == idSeleccionado) {
        this.showPokemon = true;
        this.puntuacion();
      }
      this.intentos--;
      console.log(idSeleccionado);
    },
    puntuacion() {
      if (this.intentos == 3) {
        this.puntaje += 5;
      } else if (this.intentos == 2) {
        this.puntaje += 2;
      } else if (this.intentos == 1) {
        this.puntaje += 1;
      }
    },
    reiniciar() {
      this.intentos = 3;
      this.puntaje = 0;
      this.cargaJuegoInicial();
    },
  },
  mounted() {
    console.log("Se monto el componente");
    this.cargaJuegoInicial();
  },
};
</script>
  
  <style>
.gana {
  color: blueviolet;
  font-weight: bold;
}
.pierde {
  color: red;
  font-weight: bold;
}
</style>