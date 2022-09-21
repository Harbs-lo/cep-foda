<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      resultado: {},
    };
  },
  methods: {
    async search() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const { data } = await axios.get(url);
      this.endereco = data;
    },
  },
};
</script>

<template>
  <main>
    <div class="busca_end">
      <h1>Busca de CEP:</h1>
      <form @submit.prevent="search" class="busca">
        <input type="text" v-model="cep" />
        <button type="submit">Buscar</button>
      </form>

      <form class="end">
        <label for="rua">Estado:</label>
        <input type="text" disabled v-model="endereco.uf" />
        <label for="rua">Cidade:</label>
        <input type="text" disabled v-model="endereco.localidade" />
        <label for="rua">Bairro:</label>
        <input type="text" disabled v-model="endereco.bairro" />
        <label for="rua">Rua:</label>
        <input type="text" disabled v-model="endereco.logradouro" />
      </form>
    </div>
  </main>
</template>
