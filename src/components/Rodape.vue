<template>
    <!-- Define o rodapé da página -->
    <footer class="rodape paragrafo">
        Desenvolvido por Alura | 2023 - Projeto fictício sem fins comerciais.
    </footer>
</template>


<style scoped>
/* Define estilos CSS para o rodapé */

/* Estilo base para o rodapé */
.rodape {
    background: var(--verde-escuro, #263A29);
    /* Cor de fundo do rodapé (verde-escuro ou #263A29 se a variável não estiver definida) */
    padding: 1.5rem 7.5rem;
    /* Espaçamento interno do rodapé (1.5rem acima/abaixo, 7.5rem à esquerda/direita) */
    display: flex;
    /* Usa um modelo de layout flexível */
    justify-content: center;
    /* Centraliza horizontalmente o conteúdo do rodapé */
    align-items: center;
    /* Centraliza verticalmente o conteúdo do rodapé */
}

/* Estilos de responsividade para o rodapé */

/* Estilos de responsividade para telas com largura máxima de 1300px */
@media only screen and (max-width: 1300px) {
    .rodape {
        padding: 1.5rem 3.75rem;
        /* Reduz o espaçamento interno do rodapé para telas menores */
    }
}

/* Estilos de responsividade para telas com largura máxima de 767px */
@media only screen and (max-width: 767px) {
    .rodape {
        padding: 1.5rem;
        /* Reduz ainda mais o espaçamento interno do rodapé para telas pequenas */
    }
}
</style>