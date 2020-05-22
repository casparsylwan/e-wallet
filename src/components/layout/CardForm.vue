<template>
    <div 
        class="card-form" 
        @click="$emit('up-card', card)">
        <div class="input-box number big">
            <label for="">card number</label>
            <input v-model="cardNumber" type="text" v-on:change="cardChoice(opt)">
        </div>
        <div class="input-box name big">
            <label >name</label>
            <input v-model="name" type="text" v-on:change="cardChoice(opt)">
        </div>
        <div class="small">
            <div class="input-box valid sm">
                <label >VALID THRU</label>
                <input v-model="valid" type="text" v-on:change="cardChoice(opt)">
            </div>
            <div class="input-box ccv sm" v-on:change="cardChoice(opt)" >
                <label>CCV</label>
                <input v-model="ccv" type="text" >
            </div>
        </div>
        <div class="input-box number big">
            <label for="">Vendor</label>
            <div class="select" v-on:click="showOpt()">
                <div 
                        v-on:click="cardChoice(option)"
                        v-bind:key="option.id" 
                        v-for="option in options" 
                        class="opt" :class="open">
                        <div class="circle-around" :class="option.type">
                            <Bitcoin
                                    v-if="option.id==1" 
                                    class="coin">
                                    </Bitcoin>
                            <BlockChain v-if="option.id==2" class="coin"></BlockChain>
                            <Evil v-if="option.id==3" class="coin"></Evil>
                            <Ninja v-if="option.id==4" class="coin"></Ninja>
                        </div>
                            <h2>
                              {{ option.name }}  
                            </h2>                       
                    </div>    
                </div>            
             </div>
             {{name}}           
    </div>   
</template>
<script>
import Bitcoin from '../imgSVG/VendorBitcoin';
import BlockChain from '../imgSVG/VendorBlockchain';
import Evil from '../imgSVG/VendorEvil';
import Ninja from '../imgSVG/VendorNinja'; 

export default {
    name:"cardForm",
    components:{
         Bitcoin,
         BlockChain,
         Evil,
         Ninja
    },
    props : [ 'options', 'card'],
    methods:{
        showOpt(){

                     if(this.open==='close'){
                         this.open ='open';
                     }else{
                        this.open ='close';
                     }

            
             },
        addCustomer(){

            return {
                customerName:this.name,
                cardNumber:this.cardNumber,
                ccv:this.ccv,
                valid:this.valid,
                
            }
        },
        cardChoice(option){
            //
           if(this.open==='open' || option.open=='open'){
                this.card.id = option.id;
                this.card.name = option.name;
                this.card.type = option.type; 
                this.card.customerName = this.name;
                this.card.ccv= this.ccv;
                this.card.cardNumber = this.cardNumber;
                this.card.valid = this.valid;
                this.opt= option;
                console.log(this.card)
           }          
        },
        changName(name){
            this.name = name;
            this.card.customerName = this.name;
            console.log(this.name);
        },
        changCardnumber(cardNumber){
            this.cardNumber = cardNumber;
            this.card.cardNumber = this.cardNumber;

        }
    },
     data(){
         
         return {
             open:'close',
             name:'',
             cardNumber:'',
             ccv:'',
             valid:'',
              opt:{
                    id:1,
                    type:'bit',
                    name:'BITCOIN INC',
                    open:'open'
                }

                             
                }
            }
            
}
</script>
<style lang="scss" scoped>

    textarea:focus, input:focus, select:focus{
    outline: none;
    }

    input[type="text"], input[type="number"]{
        font-size:2rem;
        font-weight: bold;
    }
    

    .input-box{



        &.big{
            width: 90%;
            margin: 1rem auto;
        }

        &.sm{
            width: 45%;
        }
        
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-start;

            label{
                padding-bottom: 0.5rem
            }
    
    
            input{
                height: 4rem;
                width: 100%;

                border-radius:0.5rem;
                border: 1px #777 solid;
            }
    }

            .small{
                width: 90%;
                margin: 0 auto;
                display: flex;
                flex-direction: row;
                justify-content: space-between;

            }
    .select{

        position: relative;
        z-index: 2;
        height: 4rem;
        width: 100%;

        margin-bottom: 20rem;

        border-radius:0.5rem;
        border: 1px #777 solid;

        &:before{
            content:"^";
            position: absolute;
            top:30%;
            right: 5%;

            font-size: 1.5rem;
            font-weight: bold;
            font-family: Arial, Helvetica, sans-serif;

            transform: rotate(180deg);
        }

  

        .opt{

            position: absolute;
            left:0;
            right: 0;

            display: flex;
            align-items: center;
            

            

            .circle-around{
                border-radius: 100%;
                background-color: black;
                height: 4rem;
                width: 4rem;

                display: flex;
                align-items: center;
                justify-content: center;

                &.evil{
                    background-color: #ff005f;

                }

                &.block{
                    background-color: #9988dd;
                }

                &.bit{
                    background-color: #f4af37;
                }

                &.ninja{
                    background-color: #111;

                }
            }

            h2{
                font-family: Arial, Helvetica, sans-serif;
                font-weight: bold;
                font-size: 2rem;
                margin-left: 2rem;
               
            }

            &.open{
                opacity: 1;
                z-index: 3;

                @for $i from 1 through 6 {
                    &:nth-child(#{$i}n){
                    top:$i * 5rem;
                    bottom:- $i * 5rem;
                    transition: all 0.5s ease-in $i * 0.1s;
                }

            }

            }

            &.close{
                opacity: 0;
                top:0;
                bottom:0;
                z-index: -1;
                @for $i from 1 through 6 {
                    &:nth-child(-#{$i}n + 6){
                    transition: all 0.5s ease-in $i * 0.1s;
                }

            }
                
            }
            
        }

    }
           

</style>
