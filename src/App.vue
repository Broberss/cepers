<script>
import axios from "axios";
export default {
  data() {
    return {
      cep: "",
      endereco: {},
    };
  },
  methods: {
    async buscar() {
      const url = `https://viacep.com.br/ws/${this.cep}/json/`;
      const res = await axios.get(url);
      this.endereco = res.data;
    },
  },
};
</script>

<template>
  <div class="formularioInput">
    <h1>Lança o CEP</h1>
    <form @submit.prevent="buscar">
      <input v-model="cep" placeholder="CEP" type="number" />
      <button type="submit">Localize minha moradia por obséquio</button>
    </form>
  </div>
  <form class="end">
    <label for="rua">Rua</label>
    <input type="text" v-model="endereco.logradouro" />
    <label for="rua">Número</label>
    <input type="text" v-model="endereco.numero" />
    <label for="rua">Bairro</label>
    <input type="text" v-model="endereco.bairro" />
    <label for="rua">Complemento</label>
    <input type="text" v-model="endereco.complemento" />
    <label for="rua">Localidade</label>
    <input type="text" v-model="endereco.localidade" />
    <label for="rua">UF</label>
    <input type="text" v-model="endereco.uf" />
    <label for="rua">IBGE</label>
    <input type="text" v-model="endereco.ibge" />
    <label for="rua">GIA</label>
    <input type="text" v-model="endereco.gia" />
    <label for="rua">DDD</label>
    <input type="text" v-model="endereco.ddd" />
    <label for="rua">SIAFI</label>
    <input type="text" v-model="endereco.siafi" />
  </form>
  {{ endereco }}
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
  button {
    width: 45%;
    height: auto;
    border-radius: 12px;
    background-color: crimson;
    transition: 15s;
  }
  h1 {
    font-weight: 900;
    display: inline-block;
    margin-right: 25px;
  }
  input {
    border-radius: 8px;
    height: 70%;
    width: 40%;
  }
  button:hover {
    background: red;
    transform: scale(25);
  }
  form.end input {
    display: flex;
    margin: auto;
  }
  form.end label {
  }
}
</style>
