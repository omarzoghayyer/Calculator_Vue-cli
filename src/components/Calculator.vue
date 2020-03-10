<template>
  <div class="calculator-grid"  >
    
    <div type="number" class="mid-grid">{{current || '0'}} </div>
    <div @click="power" class= "btn operator">^</div>
    <div @click="sq" class= "btn operator">√</div>
    <div @click="timesthree" class= "btn operator">3x</div>
    <div @click="pi" class= "btn operator">π</div>
    <div @click="clear" class="btn">c</div>
    <div @click="sign" class="btn">+/-</div>
    <div @click="percent" class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click='append(7)' class= "btn">7</div>
    <div @click='append(8)' class= "btn">8</div>
    <div @click='append(9)' class= "btn">9</div>
    <div @click="times" class= "btn operator">X</div>
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
    previous: null,
    current: '',
    operator: null,
    operatorClicked: false,
    maxCharacters: 2,
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
    sq(){
      this.operator = x => Math.sqrt(x)
      this.previous = this.current;  
      this.operatorClicked = true;
    },
    timesthree(){
      this.operator = (a, b) => a && b * 3;
      this.previous = this.current;  
      this.operatorClicked = true;
    },
    pi(){
      this.operator = x => Math.pi(x)
      this.current ='3.141592653'
      
    },
    power(){
      this.operator = x => Math.pow(x, 2)
      this.previous = this.current;  
      this.operatorClicked = true;
    },

    append(number) {
      if(this.operatorClicked) {
        this.current ='';
        this.operatorClicked = false;
      }
        this.current = `${this.current}${number}`

  },
    dot(){
      if(this.current.indexOf('.') === -1) {
        this.append('.'); 
      }
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.previous = this.current;  
      this.operatorClicked = true;    
    },
    plus(){
      this.operator = (a, b) => a + b;
      this.previous = this.current;
      this.operatorClicked = true;    

    },
    minus(){
      this.operator = (a, b) => a - b;
      this.previous = this.current;
      this.operatorClicked = true;    

    },
    times(){
      this.operator = (a, b) => a * b;
      this.previous = this.current;
      this.operatorClicked = true;    

    },

    equal(){
      this.current = `${this.operator(
        parseFloat(this.current), 
       parseFloat(this.previous)
        )}`;
        this.previous = null;
    },
    
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
  overflow: hidden;
  background-color: rgb(237, 248, 239);
  grid-column: 1 /5;
  border: solid 1px rgb(14, 13, 13);
}
.mid-grid:hover{
  background:rgb(250, 247, 247)
}
  .btn{
      border: solid 1px rgb(194, 189, 189)
  }
  .btn:hover{
    background: rgb(182, 252, 182);
  }
  


.zero{
  grid-column: 1/3;
}
.zero:hover{
  background: rgb(248, 154, 154);
}
.operator {
  background-color: orange;
  color: white;
}

</style>
