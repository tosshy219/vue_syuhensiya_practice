<template>
  <div>
    <div v-if="quiz" class="wrapper">
      <div 
        class="block"
        v-for="source in sources" 
        :key="source.id"
        @click="checkNum(source)"
        :class="{pressed:source.checked}"
      >
        <span>{{source.number}}</span>
      </div>
    </div>

    <h1  v-show="fin" class="fini">Finish!!</h1>

    <h1 v-show="quiz">ど真ん中のブロックを見続けて，<br>目を動かさないで順にクリック！</h1>
    <h1 v-show="quiz">数字の位置はリロードごとにランダム</h1>

      <a href="" class="btn">Replay?</a>
  </div>
</template>

<script>
export default {
  data(){
    return{
      sources:[],
      currentNum:1,
      quiz:true,
      fin:false
    }
  },
  methods:{
    setNum(){
      for(let i=0;i<25;i++){
        const num={
          number:'',
          checked:false,
        };
        this.sources.push(num);
        this.sources[i].number=i+1;

      }
    },
    shuffle(arr){
      for(let i = arr.length -1;i > 0;i--){
        const j =Math.floor(Math.random() * (i+1));
        [arr[j],arr[i]]=[arr[i],arr[j]];
      }
      return arr;
    },
    checkNum(e){
      if(this.currentNum===e.number){
        console.log('ok');
        console.log(typeof e);
        console.log(e);

        this.currentNum++;
        if(this.currentNum > this.sources.length){
          this.quiz=false;
          this.fin=true;
        }
        e.checked=true;
      }else{
        console.log('no');
        console.log(e+'ではありません');
        console.log(e);


      }
    }
  },
  created:function(){
    this.setNum();
    this.shuffle(this.sources);
  },
  mounted:function(){
    console.log(this.sources);
  }

}
</script>

<style scoped>
*{
  user-select: none;
}
.wrapper{
  display: flex;
  flex-wrap: wrap;
  align-content: flex-start;
  background-color: slategrey;
  width: 320px;
  height: 320px;
  padding: 10px;
  margin: 0 auto;
}
.block{
  background-color: lightcyan;
  width: 60px;
  height:60px;
  margin: 1px;
  border:1px solid rgb(13, 18, 20);
  border-radius: 6px;
  line-height: 60px;
  cursor: pointer;
}
span{
  font-size: 30px;
  margin: 0 auto;
  color: tomato;
}
.pressed{
  background-color: tomato;
}
.btn{
  text-decoration: none;
  display: block;
  margin: 0 auto;
  margin-top: 30px;
  background-color: rgb(247, 140, 121);
  box-shadow: 0 4px 0 tomato;
  color: white;
  width: 200px;
  height: 50px;
  font-size: 30px;
  line-height: 50px;
  border-radius: 5px;
}
@media screen and (max-width: 580px){
  .wrapper{
    width: 320px;
    height: 320px;
    padding: 2px;
    margin-bottom: 30px;
  }

  .block{
    width: 60px;
    height: 60px;
    line-height: 62px;
    border-radius: 3px;
    
  }
  .btn{
    margin-top: 50px;
  }
  span{
    font-size: 30px;
  }
  h1{
    font-size: 20px;
  }
  .fini{
    font-size: 50px;
    margin-top: 50px;
  }
}

</style>