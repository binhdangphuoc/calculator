<template>
  <div class="container">
        <div id="result">{{expression}}</div>
        <div class="calculator">
            <div class="left">
                <button class="btn val" @click="addChar(7)">7</button>
                <button class="btn val" @click="addChar(8)">8</button>
                <button class="btn val" @click="addChar(9)">9</button>
                <button class="btn val" @click="addChar(4)">4</button>
                <button class="btn val" @click="addChar(5)">5</button>
                <button class="btn val" @click="addChar(6)">6</button>
                <button class="btn val" @click="addChar(1)">1</button>
                <button class="btn val" @click="addChar(2)">2</button>
                <button class="btn val" @click="addChar(3)">3</button>
                <button class="btn val" @click="addChar(0)">0</button>
                <button class="btn val" @click="addChar('.')">.</button>
                <button class="btn" value="" @click="calculate()">=</button>
            </div>
            <div class="right">
                <button class="btn" value="" @click="del()">DEL</button>
                <button class="btn" value="" @click="acc()">AC</button>
                <button class="btn" value="" @click="sin()">SIN</button>
                <button class="btn" value="" @click="cos()">COS</button>
                <button class="btn val" @click="addChar('+')">+</button>
                <button class="btn val" @click="addChar('-')">-</button>
                <button class="btn val" @click="addChar('x')">*</button>
                <button class="btn val" @click="addChar(':')">/</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Calculator',
  data(){
    return{      
      expression:''
    }
  },
  methods:{
    addChar(c){
      this.expression = this.expression + c
    },
    calculate(){
      let arr = this.expression.split(/[x:+-]/)
      if(arr.length<=1||arr[1]=='') {
        console.log(arr.length) 
        this.expression=arr[0]
        return
      }
      let ans =0
      let a = Number(arr[0])
      let b=Number(arr[1])
      let exp = this.expression.slice(arr[0].length,arr[0].length+1)
      console.log(a,typeof(a))
      console.log(exp)
      switch (exp){
        case '+':
          ans = a + b
          break;
        case '-':
          ans = a-b
          break;
        case 'x':
          ans = a*b
          break;
        case ':':
          ans = a/b
          break;
        default:
          ans = 'null'
      }
      this.expression = String(ans)
      
    },
    acc(){
      this.expression = ''
    },
    del(){
      console.log(this.expression,typeof(this.expression))
      this.expression = this.expression.slice(0,this.expression.length-1)
    },
    sin(){
      this.expression = String(Math.sin(this.expression))
    },
    cos(){
      this.expression = String(Math.cos(this.expression))
    }
  }
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  *{
    font-family: 'Times New Roman', Times, serif;
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.container{
    width: 500px;
    display: inline-block;
    align-items: center;
    
}
.container #result{
    height: 100px;
    background-color: rgb(240, 231, 231);
    border: 3px solid black;
    border-radius: 5px;
    margin-top: 5px;
    margin-bottom: 5px;
    font-size: 2rem;
    text-align: left;
    
}
.left .btn{
    width: 32%;
    height: 50px;
    border: 3px solid blue;
    border-radius: 0.5rem;
    font-size: 1rem;
}
.right .btn{
    width: 48%;
    height: 50px;
    border: 3px solid blue;
    border-radius: 0.5rem;
    font-size: 1rem;
}
.calculator{
    display: flex;
    flex-wrap: nowrap;
    
}
.right{
    width: 40%;
}
.left{
    width: 60%;
}
</style>
