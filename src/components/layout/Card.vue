<template>
    <div class="card" :class="card.type" v-if="card.id!=null">
        <ChipDark class="chip" v-bind:type="card.type"></ChipDark>
        <Bitcoin v-if="card.id==1" class="coin"></Bitcoin>
        <BlockChain v-if="card.id==2" class="coin"></BlockChain>
        <Evil v-if="card.id==3" class="coin"></Evil>
        <Ninja v-if="card.id==4" class="coin"></Ninja>
        <div class="card-text" :class="card.type">
            <p>xxxx</p> 
            <!--
                {{ giveDigits(0,4) }}
                -->
            <p>xxxx</p>
<!--
{{ giveDigits(4,8) }}
    -->

            <p>xxxx</p>
<!--
{{ giveDigits(8,12) }}
    -->

            <p>xxxx</p>  
<!--            
{{ giveDigits(12, 16) }}
-->
        </div>
        <div class="valid" :class="card.type">
            <h3>VALID THRU</h3>
            <div class="name" :class="card.type">
                <span>{{ giveValidDate(0, 2) }}/{{ giveValidDate( 2, 5) }} </span>
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
    props: ["card"],
     data(){
         
         return {
             digits:['x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x'],
             validDate:['M','M','Y','Y']

         }
     },
    methods : {
        giveDigits(start, end){
            
            if(this.card.cardNumber){
                let len =  this.card.cardNumber.length;
                this.digits = ['x','x','x','x','x','x','x','x','x','x','x','x','x','x','x','x'];
                if(len>16) len = 16;
                for(let i=0; i<len; i++){
                    
                    this.digits[i] = this.card.cardNumber[i];

                }
            }
            return this.digits.slice(start, end).join('');

        },

        giveValidDate(start, end){

            if(this.card.valid){

                this.validDate = ['M','M','Y','Y'];
                let len = this.card.valid.length
                if(len>4) len = 4;
                for(let i=0; i<len; i++){
                    this.validDate[i] = this.card.valid[i];
                }
            }

            return this.validDate.slice(start, end).join('');
        }
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
        
    
        &.ninja{
        background-color: #111;
        }
        
        &.bit{
        background-color: #f4af37;
        }

        &.evil{
            background-color: #ff005f;

            -webkit-box-shadow: 26px 25px 59px -46px rgba(190,194,203,0.75);
            -moz-box-shadow: 26px 25px 59px -46px rgba(190,194,203, 0.75);
            box-shadow: 26px 25px 59px -46px rgba(190,194,203,0.75);

        text-shadow: 1px 1px 0px rgba(190,194,203,0.3);
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

        &.ninja p{
            color: #aaa;
        }

       
    }


  .hold{
      grid-area: hold;
      color:#000;

      &.block, &.evil{
          color:#333;
      }
      
    .name{
        display: flex;
        justify-content: flex-start;
        font-size: 1.5rem;
        font-weight: bold;

        &.ninja{
            color:#999;
        }

        &.bit, &.block, &.evil{
            color: #000;
        }
   
        span:nth-child(2){
            margin-left: 1rem;                        
        }
    }


  }

  .valid{
      grid-area: valid;
      
      .name{
        display: flex;
        justify-content: flex-start;
        font-size: 1.5rem;
        font-weight: bold;

        &.ninja{
            color:#999;
        }

        &.bit, &.block, &.evil{
            color:#000;
        }
   
        span:nth-child(2){
             margin-left: 1rem;                        
        }
      }
  }

  h3{
        color:#999;
    
    }

  .bit h3, .block h3, .evil h3{
        color:#000;
    }
   

</style>