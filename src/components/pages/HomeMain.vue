<template>
    <div class="homeMain">
        <CardStack v-bind:cards="cards" class="card"></CardStack>
        <div class="add-card" @click="addCard()">
            <p >
               ADD A NEW CARD 
            </p>            
        </div>
    </div>   
</template>
<script>
import CardStack from '../layout/CardStack';

export default {

     components:{
        CardStack
    }
     ,
     props: ["cards"],
     methods :{
        addCard(){
            
            this.$emit('add-the-card', 2)
        }
     }
        
    
}
</script>
<style lang="scss" scoped>
    .card{
        margin: 0 auto;
    }

    .add-card{
        margin: 0 auto;
        width: 90%;
        border: solid black 1px;
        border-radius: 1rem;

        display: flex;
        align-items: center;
        justify-content: center;

        p{
           font-size: 1.5rem;
            font-weight: bolder;
            font-family: Arial, Helvetica, sans-serif; 
            margin: 1rem;
            padding: 1rem;
        }

        

    }

</style>