<template>
    <div class="card-form">
        <div class="input-box number big">
            <label for="">card number</label>
            <input type="number">
        </div>
        <div class="input-box name big">
            <label for="">name</label>
            <input type="text">
        </div>
        <div class="small">
            <div class="input-box valid sm">
                <label for="">VALID THRU</label>
                <input type="text">
            </div>
            <div class="input-box ccv sm">
                <label for="">CCV</label>
                <input type="text">
            </div>
        </div>
        <div class="input-box number big">
            <label for="">Vendor</label>
            <div class="select" v-on:click="showOpt()">
                <div 
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
    methods:{
        showOpt(){

                     if(this.open==='close'){
                         this.open ='open';
                     }else{
                        this.open ='close';
                     }

            
             }
    },
     data(){
         
         return {
             open:'close',
             options:[
                 {
                     id:1,
                    type:'bit',
                    name:'BITCOIN INC'
                    },
                 {
                     id:2,
                     type:'block',
                     name:'BLOCK CHAIN INC'
                     },
                 {
                     id:3,
                     type:'evil',
                     name:'EVIL CORP'
                },
                 {
                     id:4,
                    type:'ninja',
                    name:'NINJA BANK'
                    }
                 ]                
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

        margin-bottom: 60rem;

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
                @for $i from 1 through 6 {
                    &:nth-child(-#{$i}n + 6){
                    transition: all 0.5s ease-in $i * 0.1s;
                }

            }
                
            }
            
        }

    }
           

</style>
