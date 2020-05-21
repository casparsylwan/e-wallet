<template>
  <div class="home">
    <HomeMain v-bind:cards="cards" v-if="page===1"></HomeMain>
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
                type:'bit'
                }
                ,
                {
                id:2,
                type:'block'
                }
                ,
                {
                id:3,
                type:'evil'
                }
                ,
                {
                id:4,
                type:'ninja'
                }],
                page:2

        }
  }
}
</script>
