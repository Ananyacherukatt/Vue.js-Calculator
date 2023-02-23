<template>
  <div class="calculator">
    <div class="display">{{ current || 0 }}</div>
    <div @click="sin" class="btn1">Sin</div>
    <div @click="factorial()" class="btn1">X!</div>
    <div @click="openBracket" class="btn2">(</div>
    <div @click="closeBracket" class="btn2">)</div>
    <div v-on:click="percentage" class="btn2">%</div>
    <div @click="clear" class="btn4">C</div>
    <div @click="cos" class="btn1">Cos</div>
    <div @click="ln" class="btn1">ln</div>
    <div v-on:click="append('7')" class="btn3">7</div>
    <div v-on:click="append('8')" class="btn3">8</div>
    <div v-on:click="append('9')" class="btn3">9</div>
    <div @click="divide" class="btn5">/</div>
    <div @click="tan" class="btn1">tan</div>
    <div @click="log" class="btn1">log</div>
    <div v-on:click="append('4')" class="btn3">4</div>
    <div v-on:click="append('5')" class="btn3">5</div>
    <div v-on:click="append('6')" class="btn3">6</div>
    <div @click="multiply" class="btn5">*</div>
    <div @click="pi" class="btn1">pi</div>
    <div @click="squareRoot" class="btn1">sqrt</div>
    <div v-on:click="append('1')" class="btn3">1</div>
    <div v-on:click="append('2')" class="btn3">2</div>
    <div v-on:click="append('3')" class="btn3">3</div>
    <div  @click="minus" class="btn5">-</div>
    <div @click="re" class="btn2">Re</div>
    <div @click="power" class="btn1">x^y</div>
    <div v-on:click="append('0')" class="btn3">0</div>
    <div  @click="dot" class="btn2">.</div>
    <div @click="equal" class="btn2">=</div>
    <div @click="add" class="btn5">+</div>

    
  </div>
  </template>

<script>
export default {
  data() {
    return {
      previous: null,
      current: '1234',
      operator: null,
      operatorClicked:false,
    }
  },
  methods: {
    clear() {
      this.current= '';
      
    },
    percentage() {
      this.current = parseFloat(this.current)/100;
      console.log(this.current)
    },
    append(number) {
      if (this.operatorClicked) {
        this.current ='';
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      if(this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },
    setPrevious() {
      this.previous = this.current;
      // this.operatorClicked=true;
    },
    divide () {
      this.current+='/';
      this.operator =(a,b) => a/b;
      this.setPrevious();
    },
    add() {
      this.current+='+';
      this.operator =(a,b) => a+b;
      this.setPrevious();

      
    },
    power() {
      this.current+='^';
      this.operator =(a,b) => Math.pow(b,a);
      this.setPrevious();
    },
    minus() {
      this.current+='-';
      this.operator =(a,b) => a-b;
      this.setPrevious();
      
    },
    multiply() {
      this.current+='*';
      this.operator =(a,b) => a*b;
      this.setPrevious();
      
    },
    openBracket () {
      this.current +=  "(";
    },
    closeBracket () {
      this.current +=  ")";
    },
    equal() {
      console.log(this.current,'hello',this.current,this.previous)
      // this.current =`${this. operator(
      //   parseFloat(this.current),
      //   parseFloat(this.previous)
      // )}`;
        this.current=eval(this.current);
        this.reVal=this.current;
        this.previous = null;



    },
    factorial() {
      var number = 1;
  if (this.current === 0) {
    this.current = "1";
  } else if (this.current < 0) {
    this.current = NaN;
  } else {
    var number = 1;
    for (var i = this.current; i > 0; i--) {
      number *=  i;
    }
    this.current = number;
  }
    },
    sin () {
      this.current = Math.sin(this.current);
      console.log(this.current);
    },
    squareRoot() {
      this.current = Math.sqrt(this.current);
    },
    cos () {
      this.current = Math.cos(this.current);
    },
    tan() {
      this.current = Math.tan(this.current);
    },
    pi () {
      this.current = (this.current * Math.PI);
    },
    ln () {
      this.current = Math.log(this.current);
    },
    re() {
      this.current+=this.reVal;
    },
    log () {
      this.current =Math.log10(this.current);
    }


  }
}
</script>

<style scoped>
.calculator {
  display: grid;
  grid-template-columns: repeat(5,1fr);
  grid-auto-rows: minmax(50px,auto);
  font-size: 25px;
  width: 740px;
  margin: 0 auto;
  background-color: antiquewhite;
  border-radius: 20px;
}
.display {
  grid-column: 1 /7;
  background-color: pink;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 10px;
  height: 60px;
  text-align: end;
  border: 1px solid black;
}
.btn1 {
  background-color: aquamarine;
  border-radius: 5px;
  margin-bottom: 10px;
  margin-left: 10px;
  margin-right: 10px;
  width: 100px;
  text-align: center;
  border: 1px  rgb(93, 185, 154) solid;

}

.btn2 {
  background-color: rgb(215, 191, 238);
  border-radius: 5px;
  margin-bottom: 10px;
  margin-left: 10px;
  margin-right: 10px;
  width: 100px;
  text-align: center;
  border: 1px  rgb(178, 117, 235)solid;
}

.btn4 {
  background-color: red;
  border-radius: 5px;
  margin-bottom: 10px;
  margin-left: 10px;
  margin-right: 10px;
  width: 100px;
  text-align: center;
  color: white;

}
.btn3 {
  background-color: rgb(108, 147, 225);
  border-radius: 5px;
  margin-bottom: 10px;
  margin-left: 10px;
  margin-right: 10px;
  width: 100px;
  text-align: center;
  border: 1px  rgb(30, 79, 177)solid;
}

.btn5 {
  background-color: rgb(173, 143, 8);
  border-radius: 5px;
  margin-bottom: 10px;
  margin-left: 10px;
  margin-right: 10px;
  width: 100px;
  text-align: center;
}
</style>
