<template>
  <div id="container">
    <Header :len="length"></Header>
    <h3>Quotes</h3>
    <textarea v-model="text" />
    <br/>
    <button @click="create"> create quote </button>
    <Display v-if='quotes.length > 0' >
      <span  v-for="(value,i) in quotes" :key="value" @click="deleting(i)" class="styledText">{{value}}</span>
    </Display>
    <div class="info">Info :  Click on the quotes to delete it</div>
  </div>
</template>

<script>
// @ is an alias to /src
import Display from "@/components/Display.vue"
import Header from "@/components/Header.vue";

export default {
  name: "home",
  data(){
    return{
      length:0,
      text:"",
      quotes:[],
      show:false,
      maxQuotes:10
    }
  },
  methods:{
    create(){
      if((this.length/10)<this.maxQuotes){
        this.quotes.push(this.text)
        this.length+=10
      }else{
        alert("delete some quotes")
      }
    },
    deleting(index){
      this.quotes=this.quotes.filter((e,i)=>i!=index)
      this.length=this.quotes.length*10
    }
  },
  components: {
    Header,
    Display
  }
};
</script>

<style scoped>
  button{
    margin-bottom: 30px;
  }
  #container{
    height: 100vh;
  }
  .styledText{
    margin:20px;
    padding:10px;
    font-style: italic;
    background: pink;
    color:white;
    font-size:28px;
    cursor: pointer;
  }
  .styledText:hover{
    background: red;
  }
  textarea{
    width:30%;
    height:10%;
    font-size: 25px;
  }
  button{
    margin:20px;
    padding:5px;
    font-size: 17px;
  }
  .info{
    width:100%;
    padding: auto 20%;
  }
</style>