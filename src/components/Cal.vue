<template>
  <div class="container">
    <div class="left">
      <input type="number" v-model.number="number" @input="cal" />
    </div>
    <div class="mid">
      <select v-model.number="kind" @change="cal">
        <option value="1">isPrime</option>
        <option value="2">isFibonacci</option>
      </select>
    </div>
    <div class="right">{{ result }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      result: "false",
      numb: null,
      kind: 1,
      primeNumber: [],
    };
  },
  computed: {
    number: {
      set(newValue) {
        this.numb = Math.round(newValue);
        if (this.numb < 0) this.numb = 1;
      },
      get() {
        return this.numb;
      },
    },
  },
  methods: {
    cal() {
      if (this.kind === 1) {
        this.result = this.isPrime();
      } else {
        this.result = this.isFibonacci();
      }
    },
    isPrime() {
      if (this.numb === 2) return true;
      if (this.numb <= 1 || this.numb % 2 === 0) return false;
      let result = true;
      const lastNumber = Math.round(Math.sqrt(this.numb));
      for (let i = 3; i <= lastNumber; i += 2) {
        if (this.numb % i === 0) {
          return false;
        }
      }
      return result;
    },
    isFibonacci() {
      if (this.numb === 0 || this.numb === 1) return true;
      let start = 0;
      let end = 1;
      console.log("fib", 0);
      console.log("fib", 1);
      while (end <= this.numb) {
        const fib = start + end;
        if (fib === this.numb) return true;
        start = end;
        end = fib;
      }
      return false;
    },
  },
};
</script>

<style scoped>
.container {
  display: grid;
  overflow: scroll;
  grid-template: "left mid right" auto / 200px minmax(100px, 1fr) 300px;
}
.left {
  grid-area: left;
  /* background-color: red; */
}
.mid {
  grid-area: mid;
  /* background-color: green; */
}
.right {
  grid-area: right;
  /* background-color: rgb(112, 250, 238); */
}
::-webkit-scrollbar {
  -webkit-appearance: none;
  width: 7px;
}

::-webkit-scrollbar-thumb {
  border-radius: 2px;
  background-color: rgba(0, 0, 0, 0.5);
  box-shadow: 0 0 1px rgba(255, 255, 255, 0.5);
}
</style>
