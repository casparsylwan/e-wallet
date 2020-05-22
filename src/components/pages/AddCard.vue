<template>
    <div class="add-card">
        <Top v-bind:page="page"></Top>
        <Card 
            v-bind:card="card" 
            class="card" ></Card>
        <CardForm
            v-bind:options="options"
            @up-card="upDateCard"
            @update-card="upDateCard"
            v-on:add-the-card="send">
        </CardForm>        
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
        CardForm,
        Card
  },
  props : ["cards", "page"],
  data () {
    return {
            
             card:{
                    id:1,
                    type:'bit',
                    name:'BITCOIN INC',
                    cardNumber:'',
                    valid:'',
                    customerName:''
             },
             options:[
                 {
                    id:1,
                    type:'bit',
                    name:'BITCOIN INC',
                    cardNumber:'',
                    valid:'',
                    customerName:''
                    
                    },
                 {
                     id:2,
                     type:'block',
                     name:'BLOCK CHAIN INC',
                    cardNumber:'',
                    valid:'',
                    customerName:''
                    
                     },
                 {
                     id:3,
                     type:'evil',
                     name:'EVIL CORP',
                    cardNumber:'',
                    valid:'',
                    customerName:''
                    
                },
                 {
                    id:4,
                    type:'ninja',
                    name:'NINJA BANK',
                    cardNumber:'',
                    valid:'',
                    customerName:''
                    
                    }
                 ]      
    }
   
  },
     methods:{
         upDateCard(card){
             
             this.card.id = card.id;
             this.card.cardNumber = card.cardNumber;
             this.card.name = card.name;
             this.card.type = card.type;
             this.card.valid = card.valid;
             this.card.customerName = card.customerName;
             


         },
         send(){
             
             this.$emit('add-the-card', this.card);
         }
     } 
}
</script>
<style lang="scss" scoped>

    .card{
        margin: 0 auto;
    }
  
</style>