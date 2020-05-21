<template>
    <h1>{{ heading() }}</h1>   
</template>
<script>
export default {
    name:"Top",
    methods:{
        heading : function(){
            return 'E-WALLETT';
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