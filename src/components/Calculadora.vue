<script setup>
import { reactive } from 'vue';

const estado = reactive ({
    campoUm: '',
    campoDois: '',
    operacoes: {
    adicao: (a, b) => a + b,
        subtracao: (a, b) => a - b,
       multiplicacao: (a, b) => a * b,
        divisao: (a, b) => a / b,
    },
    resultado: 0,
});
//definido objeto react

const calculaResultado = () => {
    const { campoUm, campoDois, operacao } = estado;
    estado.resultado = estado.operacoes[operacao](parseFloat(campoUm), parseFloat(campoDois));
};
</script>

<template>
<div class="container">
<h1>Calculadora Aritmética</h1>

    <input type="number" v-model="estado.campoUm" @input="calculaResultado">
    <input type="number" v-model="estado.campoDois" @input="calculaResultado">

    <h2>Escolha a operação desejada</h2>
    <select v-model="estado.operacao" @change="calculaResultado">
        <option value="adicao">Adição</option>
        <option value="subtracao">Subtração</option>
        <option value="multiplicacao">Multiplicação</option>
        <option value="divisao">Divisão</option>
    </select>

    <h2>Resultado: {{ estado.resultado }}</h2>
</div>
</template>

<style scoped>

* {
    padding: 0;
    margin: 0 auto;
}
.container {
    text-align: center;
}

h1 {
    font-size: 36px;
    margin: 32px;
}

h2 {
    font-size: 26px;
}

h2,
select
    {
    margin-bottom: 16px;
}

input,
select {
    width: 120px;
    height: 24px;
    text-align: center;
}

input {
    margin-bottom: 24px;
    display: flex;
}
</style>
