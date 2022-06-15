<script>
import { v4 as uuid} from "uuid";
export default {
  data() {
    return {
      novo_filme: "",
      novo_livro: "",
      filmes: [
        { id: "9a7c7c02-874d-4556-8a13-4a33c56571d1", name: "A Cinco Passos de Você", livroid: "1" },
        { id: "475f6d39-5a56-4442-8a2d-5ceba6b4b807", name: "Orgulho e Preconceito", livroid: "2" },
        { id: "874b37b6-3546-4c05-bc54-5d0fdb886d16", name: "Através da Minha Janela", livroid: "3" },
        { id: "9b35ce67-a4ec-45a0-be67-1983e37bd723", name: "Como Eu Era Antes de Você", livroid: "4" },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_filme !== ""){
      const novo_id=uuid();
      this.filmes.push({
        id: novo_id,
        name: this.novo_filme,
        livroid: this.novo_livro,
      });
        this.novo_filme = "";
        this.novo_livro = "";
      }
    },
    excluir(filme){
      const indice = this.filmes.indexOf(filme);
      this.filmes.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Filmes</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder="Nome" v-model="novo_filme" @keypress.enter="salvar" />
      <input type="text" placeholder="ID Livro" v-model="novo_livro" @keypress.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-items">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Livro ID</th>
            <th>Ação</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="filme in filmes" :key="filme.id">
            <td>{{filme.id}}</td>
            <td>{{filme.name}}</td>
            <td>{{filme.livroid}}</td>
            <td>

              <button @click="excluir(filme)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style></style>
