<script lang="ts">
// Define o componente BotaoPrincipal como um componente Vue
export default {
    // Declara as propriedades (props) do componente
    props: {
        texto: { type: String, required: true } // Define a propriedade 'texto' como uma string obrigatória
    }
}
</script>


<template>
    <!-- Define o botão principal -->
    <button class="paragrafo-lg botao-principal ">
        {{ texto }} <!-- Exibe o texto recebido como propriedade no botão -->
    </button>
</template>


<style scoped>
/* Define estilos CSS para o botão principal */

/* Estilo base para o botão principal */
.botao-principal {
    width: 19.5rem;
    /* Define a largura do botão */
    height: 3.5rem;
    /* Define a altura do botão */
    padding: 0.5rem 1rem;
    /* Adiciona espaço interno ao botão */
    border-radius: 2rem;
    /* Define bordas arredondadas para o botão */
    font-weight: 700;
    /* Define o peso da fonte do texto */
    color: var(--creme, #FFFAF3);
    /* Define a cor do texto do botão */
    background: var(--coral, #F0633C);
    /* Define a cor de fundo do botão */
    box-shadow: 4px 4px 15px 0px rgba(255, 115, 76, 0.25);
    /* Adiciona uma sombra ao botão */
    cursor: pointer;
    /* Muda o cursor ao passar sobre o botão */
    transition: 0.2s;
    /* Adiciona uma transição suave para mudanças de estilo */

    display: flex;
    /* Usa o modelo de layout flexível */
    justify-content: center;
    /* Centraliza horizontalmente o conteúdo do botão */
    align-items: center;
    /* Centraliza verticalmente o conteúdo do botão */
}

/* Estilo de hover para o botão principal */
.botao-principal:hover {
    background: var(--ocre-hover, #D1451E);
    /* Muda a cor de fundo ao passar o mouse sobre o botão */
}
</style>