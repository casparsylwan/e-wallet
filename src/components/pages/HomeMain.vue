<template>
    <div class="homeMain">
        Caspar
        <ChipDark></ChipDark>
        <Bitcoin></Bitcoin>
        <BlockChain></BlockChain>
        <Evil></Evil>
        <Ninja></Ninja>
        <ChipLight></ChipLight>
        <CardStack class="card"></CardStack>
    </div>   
</template>
<script>
import ChipDark from '../imgSVG/ChipDark';
import Bitcoin from '../imgSVG/VendorBitcoin';
import BlockChain from '../imgSVG/VendorBlockchain';
import Evil from '../imgSVG/VendorEvil';
import Ninja from '../imgSVG/VendorNinja';
import ChipLight from '../imgSVG/ChipLight';
import CardStack from '../layout/CardStack';

export default {

     components:{
        ChipDark,
        ChipLight,
        Bitcoin,
        BlockChain,
        Evil,
        Ninja,
        CardStack
    }
    
}
</script>
<style lang="scss" scoped>
    .card{
        margin: auto;
    }

</style>