<template>
  <div class="home">
    <HomeMain v-bind:cards="cards" v-if="page===2"></HomeMain>
    <AddCard  v-bind:cards="cards" v-if="page===2"></AddCard>  
  </div>
</template>

<script>
// @ is an alias to /src
import HomeMain from '../components/pages/HomeMain';
import AddCard from '../components/pages/AddCard';

export default {
  name: 'Home',
  components: {
    HomeMain,
    AddCard
  },
  data () {
    return {
      cards:[{
                id:1,
                type:'bit',
                name:'BITCOIN INC'
                }
                ,
                {
                id:2,
                type:'block',
                name:'BLOCK CHAIN INC'
                }
                ,
                {
                id:3,
                type:'evil',
                name:'EVIL CORP'
                }
                ,
                {
                id:4,
                type:'ninja',
                name:'NINJA BANK'
                }],
                page:2

        }
  }
}
</script>
