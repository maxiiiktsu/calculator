<template>
  <div>
    <div class="flex">
      <h1>kalkulacka</h1>
      <div class="inpts">
        <input v-model="expression" @input="updateResult" />
        <p class="result">{{ result }}</p>
      </div>
      <div class="btns">
        <button class="btn" v-for="btn in buttons" :key="btn" @click="appendSymbol(btn)">
          {{ btn }}
        </button>
        <button class="btn" @click="calculateResult">=</button>
        <button class="btn" @click="clearInput">C</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      expression: '',
      result: ''
    }
  },
  methods: {
    appendSymbol(symbol) {
      this.expression += symbol
    },
    updateResult() {},
    calculateResult() {
      try {
        this.result = eval(this.expression)
      } catch (error) {
        this.result = 'Error'
      }
    },
    clearInput() {
      this.expression = ''
      this.result = ''
    }
  },
  computed: {
    buttons() {
      return ['7', '8', '9', '4', '5', '6', '1', '2', '3', '0', '+', '-', '*', '.', '/']
    }
  }
}
</script>

<style scoped>
.btns {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  grid-template-rows: repeat(3, minmax(0, 1fr));
  align-items: center;
  justify-content: center;
  gap: 10px;
}

.inpts {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}

.result {
  margin-left: 2rem;
  border-style: solid;
  border-color: purple;
  border-width: 3px;
  padding: 2px;
  color: chartreuse;
}

.btn {
  border-style: solid;
  border-radius: 4px;
  width: 4rem;
  height: 4rem;
  font-size: 20px;
  background-color: chocolate;
  color: blue;
}

.btn:hover {
  background-color: khaki;
  color: cadetblue;
}

.flex {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
</style>
