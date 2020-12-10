<template>
  <q-page class="flex flex-center">
    <ais-instant-search
      :search-client="searchClient"
      index-name="instant_search"
    >
      <div class="search-panel">
        <div class="search-panel__filters">
          <ais-refinement-list attribute="brand" searchable />
        </div>

        <div class="search-panel__results">
          <ais-search-box placeholder="Search here…" class="searchbox" />
          <ais-hits>
            <template slot="item" slot-scope="{ item }">
              <p><ais-highlight :hit="item" attribute="name" /></p>
              <p><ais-highlight :hit="item" attribute="description" /></p>
            </template>
          </ais-hits>

          <div class="pagination"><ais-pagination /></div>
        </div>
      </div>
    </ais-instant-search>
  </q-page>
</template>

<script>
import Vue from 'vue'
import InstantSearch from 'vue-instantsearch'
import algoliasearch from 'algoliasearch/lite'
import 'instantsearch.css/themes/satellite-min.css'

Vue.use(InstantSearch)

export default {
  name: 'SearchIndex',
  data () {
    return {
      searchClient: algoliasearch(
        'latency',
        '6be0576ff61c053d5f9a3225e2a90f76'
      )
    }
  }
}
</script>
