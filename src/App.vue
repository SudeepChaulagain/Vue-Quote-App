<template>
<div class="container">
 <progressBar :quoteCount="quotes.length" :maxQuotes="maxQuotes"></progressBar>
  <newQuote @quoteAdded= "newQuote"></newQuote>
  <appQuoteGrid :quotes="quotes" @quoteDeleted ="quoteDelete"></appQuoteGrid>
    <div class="row">
        <div class="col-sm-12 text-center">
            <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
          </div>
    </div>
</div>
</template>

<script>
import QuoteGrid from'./Components/QuoteGrid.vue';
import NewQuote from'./Components/NewQuote.vue';
import Header from './Components/Header.vue';
export default {
  data () {
    return{
      quotes:['A quote!'],
      maxQuotes: 10
    }
  },
  methods:{
    // the method is created that was listened on the above quoteAdded event.
    // In above event we do not need to do such as newQuote(quote) or newQuote($event) as vue binds that implicitly.
    newQuote(quote){
      if (this.quotes.length >= this.maxQuotes) {
        alert('Delete quotes first!')
      }
      this.quotes.push(quote);
    },
    quoteDelete(index){
      this.quotes.splice(index, 1);
    }
  },
  components:{
    appQuoteGrid: QuoteGrid,
    newQuote: NewQuote,
    progressBar: Header
  }
}
</script>

<style>

</style>
