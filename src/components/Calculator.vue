<template>
  <div class="calculator-grid">
    <div class="mid-grid">1111</div>
    <div class="btn">%</div>
    <div class="btn">C</div>
    <div class="btn">+/-</div>
    <div class="btn">÷</div>
    <div class= "btn">7</div>
    <div class= "btn">8</div>
    <div class= "btn">9</div>
    <div class= "btn">x</div>
    <div class= "btn">4</div>
    <div class= "btn">5</div>
    <div class= "btn">6</div>
    <div class= "btn">-</div>
    <div class= "btn">1</div>
    <div class= "btn">2</div>
    <div class= "btn">3</div>
    <div class= "btn">+</div>
    <div class=" btn zero">0</div>
    <div class= "btn">.</div>
    <div class= "btn">=</div>
  </div>
</template>

<script>
export default {
}
</script>



<style scoped>
.calculator-grid{
  margin: 0 auto;
  width: 400px;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4,1fr);
  grid-auto-rows: minmax(30px, auto);
  background-color: rgb(255, 255, 255);
  
  
}
.mid-grid{
  background-color: rgb(185, 174, 174);
  grid-column: 1 /5;
  border: solid 1px black;

}
.btn {
  border: solid 1px black
}
.zero{
  grid-column: 1/3;

  
}
</style>
