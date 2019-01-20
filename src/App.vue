<template>
 <div class="calculator">
<div class="display">{{current|| '0'}}</div>
<div class="btn" @click="clear">AC</div>
<div class="btn" @click="sign">+/-</div>
<div class="btn" @click="percent">%</div>
<div class="btn operator" @click="divide">/</div>
<div class="btn" @click="append('7')">7</div>
<div class="btn" @click="append('8')">8</div>
<div class="btn" @click="append('9')">9</div>
<div class="btn operator" @click="mult">X</div>
<div class="btn" @click="append('4')">4</div>
<div class="btn" @click="append('5')">5</div>
<div class="btn" @click="append('6')">6</div>
<div class="btn operator" @click="minus">-</div>
<div class="btn" @click="append('1')">1</div>
<div class="btn" @click="append('2')">2</div>
<div class="btn" @click="append('3')">3</div>
<div class="btn operator" @click="add">+</div>
<div class="btn zero" @click="append('0')">0</div>
<div class="btn" @click="dot">(.)</div>
<div class="btn operator"  @click="equal">=</div>

 </div>
   
</template>

<script>
export default {
  name: 'calculator',
  data () {
    return{
      current:"",
      previos:null,
      operatorClicked:false,
      operator:null
    }
  },
  methods:{
    clear(){
      this.current=''
    },
    sign(){
      this.current=this.current.charAt(0)==='-'?
      this.current.slice(1):`-${this.current}`;
    },
    percent(){
      this.current=`${parseFloat(this.current)/100}`
      },
      append(number){
        if(this.operatorClicked){
          this.current='';
          this.operatorClicked=false;
        }
        this.current=`${this.current}${number}`;
      },
      dot(){
        if(this.current.indexOf('.')===-1){
          this.append('.')
        }
        
      },
      setPrevios(){
this.operatorClicked=true;
this.previos=this.current;
      },
      divide(){
this.operator=(a,b)=>b/a;
this.setPrevios();

        },
        minus(){
this.operator=(a,b)=>b-a;
this.setPrevios();

        },
        add(){
this.operator=(a,b)=>a+b;
this.setPrevios();

        },
        mult(){
this.operator=(a,b)=>a*b;
     this.setPrevios();
      },
 equal(){
this.current=`${this.operator(
  parseFloat(this.current),
  parseFloat(this.previos)
)}`;
this.previos=null;
   }
  }
}
</script>

<style>
body{
  background-image: url(https://www.kv.by/sites/default/files/pictures/mainimage/2018/08/projets.jpg);
  margin: 0;
}
.calculator{
  user-select: none;
  width:30vw;
  height: 40vw;
  margin: 0 auto;
  text-align: center;
  font-size: 5vw;
  display: grid;
  grid-template-columns: repeat(4,1fr); 
  grid-auto-rows: minmax(50px, auto);
}
.zero{
  grid-column: 1/3;
}
.display{
  text-align: center;
  grid-column: 1/5;
  background-color: #333;
  color:white;
}
.btn{
  cursor: pointer;
  background-color: antiquewhite;
  border:1px solid #999;
}
.btn:hover{
   background: rgb(232,95,76);
}
.btn:active{
  background: rgb(152,15,0);
   box-shadow: 0 3px 0 #00823F;
  top: 3px;
}
.operator{
  background-color: orange;
color:white;
}
</style>
