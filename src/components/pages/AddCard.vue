<template>
    <div class="add-card">
        <Top></Top>
        <Card v-bind:card="cards[0]" class="card" ></Card>
        <CardForm></CardForm>
        
    </div>
</template>
<script>
import Top from '../layout/Top';
import Card from '../layout/Card';
import CardForm from '../layout/CardForm';

export default {
    name:"AddCard",
    components: {
        Top,
        Card,
        CardForm
  },
  props : ["cards"]

     
}
</script>
<style lang="scss" scoped>

    .card{
        margin: 0 auto;
    }
  


</style>