<template>
    <div class="card" :class="card.type">
        <ChipDark class="chip" v-bind:type="card.type"></ChipDark>
        <Bitcoin v-if="card.id==1" class="coin"></Bitcoin>
        <BlockChain v-if="card.id==2" class="coin"></BlockChain>
        <Evil v-if="card.id==3" class="coin"></Evil>
        <Ninja v-if="card.id==4" class="coin"></Ninja>
        <div class="card-text" :class="card.type">
            <p>xxxx</p>
            <p>xxxx</p>
            <p>xxxx</p>
            <p>xxxx</p>              
        </div>
        <div class="valid" :class="card.type">
            <h3>VALID THRU</h3>
            <div class="name" :class="card.type">
                <span>10/</span><span>12</span>
            </div>
        </div>
        <div class="hold" :class="card.type">
            <h3>cardholder name</h3>
            <div class="name" :class="card.type">
                <span>first</span><span>second </span>
            </div>
        </div>
    </div>
</template>
<script>
    import ChipDark from '../imgSVG/ChipDark';
    import Bitcoin from '../imgSVG/VendorBitcoin';
    import BlockChain from '../imgSVG/VendorBlockchain';
    import Evil from '../imgSVG/VendorEvil';
    import Ninja from '../imgSVG/VendorNinja'; 

    export default {
        name:"Card"
        ,
         components:{
         ChipDark,
         Bitcoin,
         BlockChain,
         Evil,
         Ninja
    },
    props: ["card"]
        }
</script>
<style lang="scss" scoped>

    .card{
        height: 15rem;
        max-width: 25rem;
        padding: 1rem;
        background-color: #aff;
        border-radius: 1rem;

        border-top: solid 1px black;

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

    .card{
    
        &.ninja{
        background-color: #111;
        }
        
        &.bit{
        background-color: #f4af37;
        }

        &.evil{
            background-color: #aa005f;
        }

        &.block{
            background-color: #9988dd;
        }

    }

    


    .ship{
        grid-area: chip;
        padding: 1rem;
    }

    .coin{
        grid-area: coin;
        justify-self: end;

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

    .card-text.ninja{
        p{
            color: #aaa;
        }
    }

  .hold{
      grid-area: hold;
    //  color:#000;
    .name{
        display: flex;
        justify-content: flex-start;
        font-size: 1.5rem;
        font-weight: bold;

            span:nth-child(2){
                margin-left: 1rem;                        
            }
    }

    .hold.ninja{
        color:#fff;
    }


  }

  .valid{
      grid-area: valid;
      
      .name{
        display: flex;
        justify-content: flex-start;
        font-size: 1.5rem;
        font-weight: bold;

            span:nth-child(2){
                margin-left: 1rem;                        
            }
      }
  }

  .name.ninja, h3{
       color:#999;
    
  }
   

</style>