<template>
    <div class="card">
        <ChipDark class="chip"></ChipDark>
        <Bitcoin v-if="true" class="coin"></Bitcoin>
        <div class="card-text">
            <p>xxxx</p>
            <p>xxxx</p>
            <p>xxxx</p>
            <p>xxxx</p>              
        </div>
        <div class="valid">
            <h3>VALID THRU</h3>
            <div class="name">
                <span>10/</span><span>12</span>
            </div>
        </div>
        <div class="hold">
            <h3>cardholder name</h3>
            <div class="name">
                <span>first</span><span>second</span>
            </div>
        </div>
    </div>
</template>
<script>
    import ChipDark from '../imgSVG/ChipDark';
    import Bitcoin from '../imgSVG/VendorBitcoin';

    export default {
        name:"Card"
        ,
         components:{
         ChipDark,
        // ChipLight,
         Bitcoin
        // BlockChain,
        // Evil,
        // Ninja,
        // Card
    }
        }
</script>
<style lang="scss" scoped>

    .card{
        height: 15rem;
        max-width: 25rem;
        padding: 1rem;
        background-color: #aff;
        border-radius: 1rem;

        -webkit-box-shadow: 26px 25px 59px -46px rgba(0,0,0,0.75);
        -moz-box-shadow: 26px 25px 59px -46px rgba(0,0,0,0.75);
        box-shadow: 26px 25px 59px -46px rgba(0,0,0,0.75);

        text-shadow: 1px 1px 0px rgba(0,0,0,0.3);

        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        grid-template-areas: 
        ". . . coin"
        "chip . . ."
        "text text text text"
        "hold hold hold valid";
        
    }

    .ship{
        grid-area: chip;
        padding: 1rem;
    }

    .coin{
        grid-area: coin;
        justify-self: end;
        align-self: start;

    }

    .card-text{
        grid-area: text;
        
        display: flex;
        justify-content: space-evenly;

        p{
           font-size: 2rem; 
           letter-spacing: 0.1rem;
           color: #000;
           
        }
    }

  .hold{
      grid-area: hold;
      color:#000;
    .name{
        display: flex;
        justify-content: start;
        font-size: 1.5rem;
        font-weight: bold;

            span:nth-child(2){
                margin-left: 1rem;                        
            }
    }


  }

  .valid{
      grid-area: valid;
      
      .name{
        display: flex;
        justify-content: start;
        font-size: 1.5rem;
        font-weight: bold;

            span:nth-child(2){
                margin-left: 1rem;                        
            }
      }
  }

  
   

</style>