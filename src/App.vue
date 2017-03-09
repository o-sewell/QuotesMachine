<template>
    <div class="container">
    	<appHeader :quoteCount="quotes.length" :maxQuotes="maxQuotes"></appHeader>
    	<NewQuote @quoteAdded="newQuote"></NewQuote>
    	<QuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"></QuoteGrid>
    	<div class="row">
    		<div class="col-sm-12 text-center">
    			<div class="alert alert-info"> 
				Info: Click on a Quote to Delete it!
    			</div>
    		</div>
    	</div>
    </div>
</template>

<script>

    import Header from './components/Header.vue'
    import QuoteGrid from './components/QuoteGrid.vue'
    import NewQuote from './components/NewQuote.vue'

    export default {
        data() {
        	return {
        		quotes: [
        			" 'Normality is a paved road; it’s comfortable to walk on, but no flowers grow on it.' - Vincent Van Gogh "
        		],
        		maxQuotes: 10
        	}
        },
        methods: {
        	newQuote(quote) {
        		if(this.quotes.length >= this.maxQuotes) {
        			return alert('Please delete quotes first!')
        		}
        		this.quotes.push(quote)
        	},
        	deleteQuote(index) {
        		this.quotes.splice(index, 1)
        	}
        },
        components: {
        	QuoteGrid, 
        	NewQuote,
        	appHeader : Header
        }
    }
</script>

<style>
</style>
