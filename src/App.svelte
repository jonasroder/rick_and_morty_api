<script>
  import Personagem from "./componentes/Personagem.svelte";

  let personagens = [];
  let page = 1;

  async function carregarPersonagens() {
    const resposta = await fetch(
      `https://rickandmortyapi.com/api/character?page=` + page
    );
    const dados = await resposta.json();
    console.log(dados);
    personagens = dados.results;
  }
  carregarPersonagens();

  function proximaPagina() {
    page++;
    carregarPersonagens();
  }

  function paginaAnterior() {
    if (page > 1) {
      page--;
      carregarPersonagens();
    }
  }
</script>

<h1 class="title">Rick and Morty Svelte</h1>

<div class="container">
  <div class="btns">
    <button class="btn" on:click={paginaAnterior} disabled={page === 1}>Anterior</button>
    <button class="btn" on:click={proximaPagina}>Próximo</button>
  </div>

  <div class="grid">
    {#each personagens as personagen}
      <Personagem {personagen} />
    {/each}
  </div>
</div>
