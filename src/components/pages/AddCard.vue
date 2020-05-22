<template>
    <div class="add-card">
        <Top></Top>
        <Card 
            v-bind:card="card" 
            class="card" ></Card>
            {{ card }}
        <CardForm
            v-bind:options="options"
            v-bind:card="card"
            v-on:up-card="upDateCard(card)"></CardForm>
    </div>
</template>
<script>
import Top from '../layout/Top';
import Card from '../layout/Card';
import CardForm from '../layout/CardForm';

export default {
    name:"AddCard",
    components: {
        Top,
        Card,
        CardForm
  },
  props : ["cards"],
  data () {
    return {
            
             card:{
                    id:1,
                    type:'bit',
                    name:'BITCOIN INC'
             },
             options:[
                 {
                    id:1,
                    type:'bit',
                    name:'BITCOIN INC'
                    
                    },
                 {
                     id:2,
                     type:'block',
                     name:'BLOCK CHAIN INC'
                    
                     },
                 {
                     id:3,
                     type:'evil',
                     name:'EVIL CORP'
                    
                },
                 {
                    id:4,
                    type:'ninja',
                    name:'NINJA BANK'
                    
                    }
                 ]      
    }
   
  },
     methods:{
         upDateCard(card){
             this.card = card;

         }
     

     } 
}
</script>
<style lang="scss" scoped>

    .card{
        margin: 0 auto;
    }
  


</style>