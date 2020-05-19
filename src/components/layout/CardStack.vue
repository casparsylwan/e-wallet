<template>
    <div class="cardStack"> 
        abc 
        
        <Card></Card>
    
    </div> 
</template>
<script>
import Card from '../layout/Card';

export default {
    name:"CardStack",

     components:{
         Card
     }
    
}
</script>
<style lang="scss" scoped>

    .cardStack{
        padding: 1rem;
        border: solid black 1px;
    }

</style>