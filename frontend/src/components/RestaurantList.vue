<template>
<div id="restaurant-list">
  <section class="section" id="solna-restaurants" v-if="(list_type === 'both' || list_type === 'solna') && sortedSolna.length > 0">
    <h4 class="title is-4">Solna</h4>
    <restaurant-entry v-for="restaurant in sortedSolna"
                      :key="restaurant.name"
                      :restaurant_info="restaurant">
    </restaurant-entry>
  </section>
  <section class="section" id="uppsala-restaurants" v-if="(list_type === 'both' || list_type === 'uppsala') && sortedUppsala.length > 0">
    <h4 class="title is-4">Uppsala(BMC)</h4>
    <restaurant-entry v-for="restaurant in sortedUppsala"
                      :key="restaurant.name"
                      :restaurant_info="restaurant">
    </restaurant-entry>
  </section>
</div>
</template>

<script>
import RestaurantEntry from './RestaurantEntry.vue'

export default {
  name: 'RestaurantList',

  props: ['list_type', 'restaurants'],

  components: {
    'restaurant-entry': RestaurantEntry
  },

  computed: {
    sortedSolna () {
      let chosen = this.restaurants.filter((rest) => rest.campus == 'Solna')
      return chosen.sort((a,b) => (a.name > b.name) ? 1 : ((b.name > a.name) ? -1 : 0))
    },

    sortedUppsala () {
      let chosen = this.restaurants.filter((rest) => rest.campus == 'Uppsala')
      return chosen.sort((a,b) => (a.name > b.name) ? 1 : ((b.name > a.name) ? -1 : 0))
    }
  }
}
</script>

<style>

</style>
