<template>
  <b-container>
    <div class="input-group mt-5 mb-5">
      <input
        type="text"
        v-model="inputFruit"
        @keyup.enter="addFruit()"
        class="form-control"
        placeholder="Escribe aqui la fruta que quieres sumar a tu lista"
        aria-label="Recipient's username"
        aria-describedby="button-addon2"
      >
      <div class="input-group-append">
        <button
          class="btn btn-outline-secondary"
          @click="addFruit()"
          type="button"
          id="button-addon2"
        >Añadir</button>
      </div>
    </div>
    <b-container>
      <table class="table mt-3">
        <thead>
          <tr>
            <th scope="col">Nombre</th>
            <th scope="col">Cantidad</th>
            <th scope="col">➕➖</th>
            <th scope="col">Sin Stock</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="fruta of frutas" :key="fruta.id">
            <th scope="row">{{ fruta.nombre }}</th>
            <td>{{ fruta.cantidad }}</td>
            <td>
              <button class="btn btn-sm btn-info mr-1" @click="fruta.cantidad++">+</button>
              <button
                class="btn btn-sm btn-warning ml-1"
                @click="fruta.cantidad>0?fruta.cantidad--:fruta.cantidad"
              >-</button>
            </td>
            <td v-if="fruta.cantidad <= 0">✅</td>
          </tr>
        </tbody>
      </table>
    </b-container>
  </b-container>
</template>

<script>
export default {
  name: "ListadoFrutas",
  data() {
    return {
      inputFruit: ""
    };
  },
  computed: {
    arrayOrdenado() {
      let arrayOrdenado = this.frutas;
      return arrayOrdenado.sort((a, b) => b.cantidad - a.cantidad);
    }
  },
  methods: {
    addFruit() {
      let fruitInput =
        this.inputFruit.charAt(0).toUpperCase() + this.inputFruit.slice(1);
      this.frutas.push({ nombre: fruitInput, cantidad: 0 });
      this.inputFruit = "";
    }
  },
  props: ["frutas"]
};
</script>

<style scoped>
</style>
