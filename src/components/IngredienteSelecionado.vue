<script lang="ts">
import Tag from './Tag.vue'; // Importa o componente Tag

export default {
    components: { Tag }, // Registra o componente Tag para uso dentro deste componente
    props: {
        ingrediente: { type: String, required: true } // Define a propriedade 'ingrediente' como obrigatória e do tipo String
    },
    data() {
        return {
            selecionado: false // Inicializa o estado 'selecionado' como falso
        }
    },
    methods: {
        aoClicar() {
            this.selecionado = !this.selecionado; // Alterna o estado 'selecionado' ao clicar no botão

            // Emite um evento dependendo do estado selecionado
            if (this.selecionado) {
                this.$emit('adicionarIngrediente', this.ingrediente); // Emite o evento 'adicionarIngrediente'
            } else {
                this.$emit('removerIngrediente', this.ingrediente); // Emite o evento 'removerIngrediente'
            }
        }
    },
    emits: ['adicionarIngrediente', 'removerIngrediente'] // Declara os eventos emitidos pelo componente
}
</script>


<template>
    <!-- Botão representando o ingrediente -->
    <button class="ingrediente" @click="aoClicar()" :aria-pressed="selecionado">
        <!-- Componente Tag exibindo o texto do ingrediente e indicando se está selecionado -->
        <Tag :texto="ingrediente" :ativa="selecionado" />
    </button>
</template>


<style scoped>
/* Estilo para o botão de ingrediente */
.ingrediente {
    cursor: pointer; /* Altera o cursor para indicar que o botão é clicável */
}
</style>
