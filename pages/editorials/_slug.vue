<script>
import { mapState } from 'vuex'

export default {
  async fetch({ i18n, context, params, store, store: { dispatch, getters } }) {
    await dispatch('geteditorial', params)
    await dispatch('getReadMore', {
          slug: params.slug,
          tags: Object.keys(store.state.editorials.data)
   })
   await dispatch('getPrevNext', params)
  },
  computed: {
    ...mapState({
      editorial: (state) => state.editorial.data,
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
       <h4>{{editorial.name}}</h4>
	   by {{editorial.name}}</br>
	   User Rating: {{editorial.userRating}}; Year: {{editorial.year}};</br>
	   Price: {{editorial.price}}; Genere: {{editorial.genre}}
	 </div>
	 <utteranc/>
	 <div class="two columns"></div>
   </div>
   <FooterView />
 </div>
</template>