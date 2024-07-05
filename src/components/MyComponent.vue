<template>
    <div class="my-component">
        <h1 v-bind:class="{ highlighted: isHighlighted }">{{ title }}</h1>
        <h1 v-if="isVisible"> {{ message }}</h1>
        <button v-on:click="_$event => isVisible = !isVisible">Ver mensaje</button> <!-- Botón usando eventos -->
        <button v-on:click="toggleVisibility">Ver mensaje</button> <!-- Botón usando métodos -->
        <button @click="toggleHighlight">Highlight</button>
        <input v-model="message"> <!-- actualiza la variable según lo que escribas -->
        <button @click="changeMessage">Change message</button>
        <button v-on:click="sayHello">Alerta de mensaje</button> <!-- Usando métodos. También se puede @click="sayHello" -->

        <ul>
            <li v-for="item in list" :key="item.id">{{ item.text }}</li> <!-- "v-for" es una directiva -->
        </ul>
    </div>
</template>

<style scoped>
    .highlighted {
        color: gold;
    }
</style>

<script>
import { mapState, mapMutations } from 'vuex';

    export default {
        computed: {
            ...mapState(['message'])
        },
        methods: {
            ...mapMutations(['setMessage']),
            changeMessage() {
                this.setMessage('Hello everyone!!!');
            },
            toggleVisibility() {
                this.isVisible = !this.isVisible;
            },
            sayHello () {
                alert('Hello!!!');
            },
            toggleHighlight() {
                this.isHighlighted = !this.isHighlighted;
            }
        },
        name: 'MyComponent',
        data() {
            return {
                message: 'Hello with vue!',
                title: 'This is the title',
                isHighlighted: false,
                isVisible: true,
                elementList: [
                    { id: 1, text: "First item" },
                    { id: 2, text: "Second item" },
                    { id: 3, text: "Third item" },
                ]
            }
        }
    }
</script>
