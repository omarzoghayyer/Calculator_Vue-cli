<template>
  <div class="calculator-grid">
    <div class="mid-grid">{{current || '0'}}</div>
    <div @click="clear" class="btn">C</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click='append(7)' class= "btn">7</div>
    <div @click='append(8)' class= "btn">8</div>
    <div @click='append(9)' class= "btn">9</div>
    <div @click="times" class= "btn operator">x</div>
    <div @click='append(4)' class= "btn">4</div>
    <div @click='append(5)' class= "btn">5</div>
    <div @click='append(6)' class= "btn">6</div>
    <div @click="minus" class= "btn operator">-</div>
    <div @click='append(1)' class= "btn">1</div>
    <div @click='append(2)' class= "btn">2</div>
    <div @click='append(3)' class= "btn">3</div>
    <div @click="plus" class= "btn operator">+</div>
    <div @click='append(0)' class=" btn zero">0</div>
    <div @click='dot' class= "btn">.</div>
    <div @click="equal" class= "btn operator">=</div>
  </div>
</template>

<script>
export default {
  data(){
  return {
    current: '',
   }
  },
  methods: {
    clear() {
      this.current = '';
    },
    sign() {
    this.current = this.current.charAt(0) === '-' ? 
      this.current.slice(1) : `-${this.$current}`;
    },
    percent(){
      this.current = `${parseFloat(this.current)/100}`
    },
    append(number) {
      this.current = `${this.current}${number}`
  },
    dot(){
      if(this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },
    divide() {

    },
    plus(){

    },
    minus(){

    },
    equal(){
      
    }
 }
}

</script>



<style scoped>
.calculator-grid{
  margin: 0 auto;
  width: 350px;
  font-size: 45px;
  display: grid;
  grid-template-columns: repeat(4,1fr);
  grid-auto-rows: minmax(30px, auto);
  background-color: rgb(255, 255, 255);
}

.mid-grid{
  background-color: rgb(226, 218, 218);
  grid-column: 1 /5;
  border: solid 1px rgb(14, 13, 13);

}
.btn {
  border: solid 1px rgb(194, 189, 189)
}
.zero{
  grid-column: 1/3;
}
.operator {
  background-color: orange;
  color: white;
}
</style>
