<template>
    <div class="my-component">
        <h1 v-if="isVisible"> {{ message }}</h1>
        <button v-on:click="_$event => isVisible = !isVisible">Ver mensaje</button> <!-- Botón usando eventos -->
        <button v-on:click="toggleVisibility">Ver mensaje</button> <!-- Botón usando métodos -->
        <input v-model="message"> <!-- Cambia el texto según lo que escribas -->
        <button v-on:click="sayHello">Alerta de mensaje</button> <!-- Botón usando métodos -->
    </div>
</template>

<script>
    export default {
        name: 'MyComponent',
        data() {
            return {
                message: 'Hello with vue!',
                isVisible: true
            }
        },
        methods: {
            toggleVisibility() {
                this.isVisible = !this.isVisible;
            },
            sayHello () {
                alert('Hello!!!')
            }
        }
    }
</script>
