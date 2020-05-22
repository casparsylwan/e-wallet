<template>
    <h1>{{ heading() }}</h1>   
</template>
<script>
export default {
    name:"Top",
    props:['page'],
    methods:{
        heading : function(){

            if(this.page==1){
                return 'E-WALLETT';
            }else if(this.page==2){
                return 'ADD A NEW BANK CARD';
            }

            
        }

    },
     data(){
         return {
             scen:'E-WALLET'
         }
     }
}
</script>
<style lang="scss" scoped>
    h1{
        text-align: center;
        font-size: 3rem;
        font-weight: bolder;
        margin: 2rem;
        font-family: Arial, Helvetica, sans-serif;
    }


</style>