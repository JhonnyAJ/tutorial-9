<script>
import { mapState } from 'vuex'

export default {
  async fetch({ i18n, context, params, store, store: { dispatch, getters } }) {
    await dispatch('getauthor', params)
    await dispatch('getReadMore', {
          slug: params.slug,
          tags: Object.keys(store.state.authors.data)
   })
   await dispatch('getPrevNext', params)
  },
  computed: {
    ...mapState({
      author: (state) => state.author.data,
      readMore: (state) => state.readMore.data,
      prevNext: (state) => state.prevNext.data,
    })
  }
}
</script>

<template>
  <div class="container">
   <HeaderView />
   <div class="row">
     <div class="three columns">
     </div>
     <div class="six columns">
       <h4>{{author.name}}</h4>
	   by {{author.name}}</br>
	   User Rating: {{author.userRating}}; Year: {{author.year}};</br>
	   Price: {{author.price}}; Genere: {{author.genre}}
	 </div>
	 <utteranc/>
	 <div class="two columns"></div>
   </div>
   <FooterView />
 </div>
</template>