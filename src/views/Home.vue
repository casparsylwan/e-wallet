<template>
  <div class="home">
    <HomeMain 
            v-bind:cards="cards" 
            v-if="page===1"
            v-bind:page="page"
            v-on:add-the-card="newCard"></HomeMain>
    <AddCard  
            v-bind:cards="cards" 
            v-if="page===2"
            v-bind:page="page"
            v-on:add-the-card="addCard"></AddCard>  
  </div>
</template>

<script>
// @ is an alias to /src
import HomeMain from '../components/pages/HomeMain';
import AddCard from '../components/pages/AddCard';

export default {
  name: 'Home',
  components: {
    HomeMain,
    AddCard
  },
   methods:{
     addCard : function(card){
       
       
       let max = 0;
       if(this.cards.length!=0){
          max = this.cards.reduce(function(prev, current) {
                            return (prev.uniqId > current.uniqId) ? prev : current
                            });
       }
       
      card.uniqId= max + 1; 
      this.cards.push(card);  
       this.page =1;
       
     },
     newCard(){
       this.page=2;
     }
   },
  data () {
    return {
      cards:[
        //{
                // id:1,
                // type:'bit',
                // name:'BITCOIN INC',
                // uniqId:1
                // }
                // ,
                // {
                // id:2,
                // type:'block',
                // name:'BLOCK CHAIN INC'
                // }
                // ,
                // {
                // id:3,
                // type:'evil',
                // name:'EVIL CORP'
                // }
                // ,
                // {
                // id:4,
                // type:'ninja',
                // name:'NINJA BANK'
//                }
                ],
                page:2

        }
  }
}
</script>
