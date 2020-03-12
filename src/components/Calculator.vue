<template>
  <div class="calculator-grid">
  
    <button type="number" class="mid-grid">{{current}} </button>
    <button @click="power" class= "btn operator">^</button>
    <button @click="sq" class= "btn operator">√</button>
    <button @click="sin" class= "btn operator">sin</button>
    <button @click="cos" class= "btn operator">cos</button>
    <button @click="backspace" class= "btn operator">←</button>
    <button @click="tan" class= "btn operator">tan</button>
    <button @click="timesthree" class= "btn operator">3x</button>
    <button @click="pi" class= "btn operator">π</button>
    <button @click="clear" class="clear-btn">clear</button>
    <button @click="sign" class="btn">+/-</button>
    <button @click="percent" class="btn">%</button>
    <button @click="divide" class="btn operator">÷</button>
    <button @click='append(7)' class= "btn">7</button>
    <button @click='append(8)' class= "btn">8</button>
    <button @click='append(9)' class= "btn">9</button>
    <button @click="times" class= "btn operator">X</button>
    <button @click='append(4)' class= "btn">4</button>
    <button @click='append(5)' class= "btn">5</button>
    <button @click='append(6)' class= "btn">6</button>
    <button @click="minus" class= "btn operator">-</button>
    <button @click='append(1)' class= "btn">1</button>
    <button @click='append(2)' class= "btn">2</button>
    <button @click='append(3)' class= "btn">3</button>
    <button @click="plus" class= "btn operator">+</button>
    <button @click='append(0)' class=" btn zero">0</button>
    <button @click='dot' class= "btn">.</button>
    <button @click="equal" class= "btn operator equal" >=</button>

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

    //list of operators
    clear() {
      this.current = '';
    },
    sign() {
    this.current = this.current.charAt(0) === '-' ? 
      this.current.slice(1) : ('-' + this.current)
    },
    percent(){
      this.current = (this.current/100)
      this.current+= "%"

    },
    tan(){
      this.operator = x =>Math.tan(x.current);
      this.current+= "tan"

    },
    cos() {
      this.operator = x => Math.cos(x.current);
      this.current+= "cos"

    },
    sin() {
      this.operator = x => Math.sin(x.current);
      this.current+="sin"
    },
    backspace() {
      this.current = this.current.substring(0, this.current.length -1);

    },
    sq(){
      this.operator = x => Math.sqrt(x)
      this.previous = this.current;  
      this.operatorClicked = true;
      this.current+= "√"

      
    },
    timesthree(){
      this.operator = (a, b) => a && b * 3;
      this.previous = this.current;  
      this.operatorClicked = true;
    },
    pi(){
      this.operator = x => Math.pi(x)
      this.current ='3.141592653'
      this.current+= "π"
      
    },
    power(){
      this.operator = x => Math.pow(x, 2)
      this.previous = this.current;  
      this.operatorClicked = true;
      this.current+= "^"
    },

    append(number) {
 if(this.operatorClicked) {
        this.current ='';
        this.operatorClicked = false;
      }
        this.current = (this.current + number)
  },
  

  //the dot method depends on the previous append number in order for it to run.
    dot(){
      if(this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },
    divide() {
      this.operator = (a, b) => a / b;
      this.previous = this.current;  
      this.operatorClicked = true;   
      this.current+= "/" 
    },
    plus(){
      this.operator = (a, b) => a + b;
      this.previous = this.current;
      this.operatorClicked = true;   
      this.current+= "+" 

    },
    minus(){
      this.operator = (a, b) => a - b;
      this.previous = this.current;
      this.operatorClicked = true; 
      this.current+= "-" 
   

    },
    times(){
      this.operator = (a, b) => a * b;
      this.previous = this.current;
      this.operatorClicked = true; 
      this.current+= "*"   
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
  width: 300px;
  font-size: 45px;
  display: grid;
  grid-template-columns: repeat(4,1fr);
  grid-auto-rows: minmax(55px, auto);
  cursor: pointer;
}
.clear-btn {
  font-size: 25px;
  color: rgb(255, 255, 255);
  cursor: pointer;
  background-color: rgb(7, 7, 7);
  border-radius: 30px;
}

.mid-grid{
  overflow: hidden;
  border-radius: 5px;
  background-color: rgb(250, 255, 251);
  grid-column: 1 /5;
  height: 78px;
  font-size: 40px;
  cursor: pointer;
  border: solid 1px rgb(14, 13, 13);
}
.mid-grid:hover{
  background: rgb(179, 176, 171);
  cursor: pointer;
}
.btn{
  border: solid 1px rgb(134, 130, 130);
  font-size: 25px;
  cursor: pointer;
  border-radius: 30px;
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
  color: rgb(17, 16, 16);
  font-size: 25px;
  cursor: pointer;
}
.equal {
cursor: pointer;
}

</style>
