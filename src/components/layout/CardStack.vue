<template>
    <div class="cardStack"> 
        <Top></Top>
        
        <Card class="active-card" v-bind:card="cards[ide]"></Card>
        
        <div class="stack">
            <div class="payload" v-bind:key="card.uniqId" v-for="card in cards" v-on:click="showCard(card.id)">
                <Card v-bind:card="card" class="pay"></Card>
            </div>
        </div>
    </div> 
</template>
<script>
import Card from '../layout/Card';
import Top from '../layout/Top';

export default {
    name:"CardStack",

     components:{
         Card,
         Top
     },
     data(){
         return {
                ide:0
         }
     },
     methods:{
        showCard(id){

            this.ide = id;
            this.ide = this.cards.findIndex(card => card.id === id);
            return this.cards[this.ide];
        }
    }
    ,
     props: ["cards"]
}
</script>
<style lang="scss" scoped>

    .cardStack{
        padding: 1rem;
        width: fit-content;
    }

    .active-card{
        margin: 0 auto;
    }

    .stack{
        width: 100%;
        display: flex;
        flex-direction: column;
    }

    .payload{
        position: relative;
        z-index: 1;
        margin-top: -12rem;
        transition: transform 0.5s;

    }

    .payload:nth-child(-n+1){
        margin-top: 2rem;
        

    }

    .payload:hover{
        transform: translateY(-2rem);
    }


</style>