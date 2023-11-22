<template>
  <div id="app">
    <h1>Calculadora Aritmética</h1>

    <div>
      <label for="numero1">Número 1:</label>
      <input type="number" v-model="numero1" @input="validarNumero1" />
    </div>

    <div>
      <label for="numero2">Número 2:</label>
      <input type="number" v-model="numero2" @input="validarNumero2" />
    </div>

    <div>
      <label for="operacao">Operação:</label>
      <select v-model="operacao" @change="calcularResultado">
        <option value="soma">Soma (+)</option>
        <option value="subtracao">Subtração (-)</option>
        <option value="multiplicacao">Multiplicação (*)</option>
        <option value="divisao">Divisão (/)</option>
      </select>
    </div>

    <div>
      <h2>Resultado: <span>{{ resultado }}</span></h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero1: 1,
      numero2: 1,
      operacao: 'soma',
      resultado: 0,
    };
  },
  methods: {
    validarNumero1() {
      if (this.numero1 < 0) {
        alert('O valor deve ser positivo.');
        this.numero1 = 0;
      }
      this.calcularResultado();
    },
    validarNumero2() {
      if (this.numero2 < 0) {
        alert('O valor deve ser positivo.');
        this.numero2 = 0;
      }
      this.calcularResultado();
    },
calcularResultado() {
  const operations = {
    'soma': () => this.numero1 + this.numero2,
    'subtracao': () => this.numero1 - this.numero2,
    'multiplicacao': () => this.numero1 * this.numero2,
    'divisao': () => this.numero1 / this.numero2,
  };

  const operationFunc = operations[this.operacao] || (() => 0);
  this.resultado = operationFunc();
}
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #417cb7;
  margin-top: 60px;
}

label {
  font-weight: bold;
}

input {
  width: 100px;
  padding: 5px;
  margin: 5px;
}

select {
  padding: 5px;
  margin: 5px;
}

h2 {
  margin-top: 20px;
}

span {
  color: #2e353b;
}
</style>
