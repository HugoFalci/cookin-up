<template>
  <!-- Cabeçalho da página com a classe 'banner' -->
  <header class="banner">
    <div>
      <!-- Logo do site -->
      <img src="../assets/imagens/logo.svg" alt="Logo do cookin' up" class="logo">

      <!-- Frase de destaque no cabeçalho com estilo grande -->
      <p class="cabecalho-lg frase-cabecalho">
        <!-- Parte do texto com cor verde -->
        <span class="texto-verde">Um banquete de ideias para</span>
        despertar o chef que há em você!
      </p>

      <!-- Subtítulo com estilo grande -->
      <p class="subtitulo-lg">
        Explore novas receitas todos os dias com os ingredientes que estão ao seu alcance!
      </p>
    </div>
    <!-- Imagem no banner -->
    <img src="../assets/imagens/foto-banner.png"
      alt="Foto de uma mulher cozinhando com uma bacia de cidro nas mãos. ela está sorrindo e está apoiando um celular entre seu rosto e ombro"
      class="foto-banner">
  </header>
</template>

<style scoped>
/* Estilo para a classe 'banner' */
.banner {
  padding: 4rem 7.5rem;
  /* Espaçamento interno */
  color: var(--creme);
  /* Cor do texto */

  display: flex;
  /* Layout flexível */
  justify-content: space-between;
  /* Distribuição dos itens com espaço entre eles */
  align-items: center;
  /* Alinhamento vertical central */
  column-gap: 3.25rem;
  /* Espaçamento entre colunas */
}

/* Estilo para a classe 'logo' */
.logo {
  height: 4.5rem;
  /* Altura da logo */
  margin-bottom: 3rem;
  /* Margem inferior */
}

/* Estilo para a classe 'frase-cabecalho' */
.frase-cabecalho {
  margin-bottom: 2rem;
  /* Margem inferior */
}

/* Estilo para a classe 'texto-verde' */
.texto-verde {
  color: var(--verde-medio, #3D6D4A);
  /* Cor verde personalizada */
}

/* Estilo para a classe 'foto-banner' */
.foto-banner {
  width: 35rem;
  /* Largura da imagem */
}

/* Media query para telas com largura máxima de 1300px */
@media only screen and (max-width: 1300px) {
  .banner {
    padding: 4rem 3.75rem;
    /* Reduz espaçamento interno */
    flex-direction: column;
    /* Alinha itens em coluna */
    align-items: center;
    /* Centraliza itens */
    gap: 1rem;
    /* Espaçamento entre itens */
  }

  .logo {
    display: block;
    /* Exibe como bloco */
    margin-left: auto;
    /* Centraliza horizontalmente */
    margin-right: auto;
    /* Centraliza horizontalmente */
  }
}

/* Media query para telas com largura máxima de 767px */
@media only screen and (max-width: 767px) {
  .banner {
    padding: 4rem 1.5rem;
    /* Reduz ainda mais o espaçamento interno */
  }

  .foto-banner {
    width: min(100%, 21.25rem);
    /* Largura da imagem responsiva */
  }
}
</style>
